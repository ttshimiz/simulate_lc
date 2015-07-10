# simulate_lc
Python function that simulates a light curve based on the [Timmer &amp; Koenig 1995](http://adsabs.harvard.edu/abs/1995A%26A...300..707T) algorithm.

## Dependencies:
1. Python 2.0 or greater
2. numpy

## Example Usage
Make sure simulate_lc.py is in your Python path.
Open up an IPython session.
```python
import simulate_lc

# Set the mean of the simulated light curve
mlc = 0.0

# Choose a PSD model
model = 'sharp'

# Set the number of timesteps in the simulated light curve and 
# the length of each timestep in seconds.
nn = 256.
delt = 1.0

# Set the parameters of the PSD model.
# For the 'sharp' model the parameters are the normalization, the break frequency,
# the low frequency slope, the high frequency slope, and white noise level.
params = [1.0, 10**(-6), -1.0, -2.0, 0.0]

# Simulate the light curve
sim_lc = simulate_lc.lc_sim(nn, delt, mean_lc, model, params)
```
`sim_lc` is now a 1D array containing the data points of the simulated light curve.

## PSD models
The function can handle 3 different PSD models:

1. Unbroken powerlaw (`model = 'unbroken'`)
2. Sharply broken powerlaw (`model = 'sharp'`)
3. Bended knee (`model = 'slow'`)
