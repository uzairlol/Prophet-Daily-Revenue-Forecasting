# Time Series Forecasting with Prophet

This repository contains a Jupyter notebook (`forecasting_notebook.ipynb`) that implements a time series forecasting model using Facebook's Prophet library. The model forecasts economic or metric data up to June 2026, incorporating Pakistan's public and lunar holidays for improved seasonality handling. It includes hyperparameter tuning with Optuna, data preprocessing (e.g., log transformation option), and generates detailed monthly Excel summaries with weekly totals and averages. Visualization of training and validation loss curves is also included.

## Project Overview
- **Data Loading**: Loads data from a CSV file with a 'Day' column (dates) and multiple numeric metric columns.
- **Holidays Integration**: Includes fixed Gregorian holidays (e.g., Kashmir Day, Pakistan Day) and lunar holidays (e.g., Eid ul Fitr, Eid ul Adha) with approximate shifts for future years.
- **Forecasting**: Uses Prophet to forecast each metric column separately, with options for additive/multiplicative seasonality and custom monthly seasonality.
- **Hyperparameter Tuning**: Optuna is used to optimize parameters like changepoint prior scale, seasonality prior scale, and Fourier order for monthly seasonality.
- **Output Generation**: Creates an Excel file (`all_forecasts.xlsx`) with monthly sheets containing daily forecasts, weekly totals/averages, and monthly summaries.
- **Visualizations**: Plots training and validation loss curves over epochs.
- **Performance Metrics**: Evaluates models using MAE and MSE on a validation set.

**Note on Data**: The input CSV (`CONFIDENTIAL.csv` in the notebook) is confidential and not included in this repository. It contains a 'Day' column with dates and numeric columns for metrics. To run the notebook, replace the file path with your own dataset of similar structure. If you want to test with sample data, create a dummy CSV with synthetic values.

## Setup Instructions
1. Clone the repository:
   ```bash
   git clone https://github.com/uzairlol/prophet-forecasting.git
   cd prophet-forecasting
   ```
2. Install dependencies from `requirements.txt`:
   ```bash
   pip install -r requirements.txt
   ```
   Note: Prophet requires CmdStanPy for its backend. If you encounter installation issues, run:
   ```bash
   python -m cmdstanpy.install_cmdstan
   ```
3. Rename the notebook if needed (it's provided as `i_like_graphs.ipynb` but suggested rename to `forecasting_notebook.ipynb`).
4. Replace the CSV path in the notebook with your data and run the cells.

## Running the Notebook
- Open `forecasting_notebook.ipynb` in Jupyter Notebook or JupyterLab.
- Execute the cells sequentially. The notebook will:
  - Load and preprocess data.
  - Tune hyperparameters for each column.
  - Generate forecasts.
  - Create `all_forecasts.xlsx` with summaries.
  - Display loss curve plots (you can save them as images via `plt.savefig('loss_curve.png')` if desired).
- Outputs: Embedded plots in the notebook (if run and saved), Excel file for forecasts.

## Graphs and Visualizations
The notebook generates plots such as:
- Training and validation loss curves over epochs (`plt.plot(epochs, loss_callback.train_losses, ...)`).

To include graphs in the repo:
- Run the notebook and use `plt.savefig('images/loss_curve.png')` after each plot to export as PNG.
- Upload the PNG files to the repo (e.g., in an `images/` folder).
- Reference them in this README, e.g.:
  ```markdown
  ![Sample Loss Curve](images/loss_curve.png)
  ```

(If you've already run the notebook and saved outputs, GitHub will render the plots directly in the `.ipynb` file.)

## Dependencies
See `requirements.txt` for the full list. Key libraries:
- `prophet`: For time series forecasting.
- `optuna`: For hyperparameter optimization.
- `pandas`, `numpy`, `matplotlib`: For data handling and visualization.
- `openpyxl`: For Excel output formatting.

## License
This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

## Acknowledgments
- Built with [Prophet](https://facebook.github.io/prophet/) for forecasting.
- Hyperparameter tuning via [Optuna](https://optuna.org/).
- Holiday data based on Pakistan's public calendar (approximate for lunar dates).

If you encounter issues (e.g., CmdStanPy optimization errors on Windows), refer to the Prophet documentation for troubleshooting environment setup.