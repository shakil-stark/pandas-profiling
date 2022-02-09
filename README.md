# pandas-profiling
Pandas profiling is an Python module with which we can quickly do an exploratory data analysis with just a few lines of code. In short, what pandas profiling does is save us all the work of visualizing and understanding the distribution of each variable.
Installation
Using pip
PyPi Downloads PyPi Monthly Downloads PyPi Version

You can install using the pip package manager by running

pip install pandas-profiling[notebook]
Alternatively, you could install the latest version directly from Github:

pip install https://github.com/pandas-profiling/pandas-profiling/archive/master.zip
Using conda
Conda Downloads Conda Version

You can install using the conda package manager by running

conda install -c conda-forge pandas-profiling
From source
Download the source code by cloning the repository or by pressing 'Download ZIP' on this page.

Install by navigating to the proper directory and running:

python setup.py install
Documentation
The documentation for pandas_profiling can be found here. Previous documentation is still available here.

Getting started
Start by loading in your pandas DataFrame, e.g. by using:

import numpy as np
import pandas as pd
from pandas_profiling import ProfileReport

df = pd.DataFrame(np.random.rand(100, 5), columns=["a", "b", "c", "d", "e"])
To generate the report, run:

profile = ProfileReport(df, title="Pandas Profiling Report")
Explore deeper
You can configure the profile report in any way you like. The example code below loads the explorative configuration, that includes many features for text (length distribution, unicode information), files (file size, creation time) and images (dimensions, exif information). If you are interested what exact settings were used, you can compare with the default configuration file.

profile = ProfileReport(df, title="Pandas Profiling Report", explorative=True)
Learn more about configuring pandas-profiling on the Advanced usage page.

Jupyter Notebook
We recommend generating reports interactively by using the Jupyter notebook. There are two interfaces (see animations below): through widgets and through a HTML report.
Saving the report
If you want to generate a HTML report file, save the ProfileReport to an object and use the to_file() function:

profile.to_file("your_report.html")
Alternatively, you can obtain the data as JSON:

# As a string
json_data = profile.to_json()

# As a file
profile.to_file("your_report.json")
Large datasets
Version 2.4 introduces minimal mode.

This is a default configuration that disables expensive computations (such as correlations and duplicate row detection).

Use the following syntax:

profile = ProfileReport(large_dataset, minimal=True)
profile.to_file("output.html")
Benchmarks are available here.

Command line usage
For standard formatted CSV files that can be read immediately by pandas, you can use the pandas_profiling executable.

Run the following for information about options and arguments.

pandas_profiling -h
Advanced usage
A set of options is available in order to adapt the report generated.

title (str): Title for the report ('Pandas Profiling Report' by default).
pool_size (int): Number of workers in thread pool. When set to zero, it is set to the number of CPUs available (0 by default).
progress_bar (bool): If True, pandas-profiling will display a progress bar.
infer_dtypes (bool): When True (default) the dtype of variables are inferred using visions using the typeset logic (for instance a column that has integers stored as string will be analyzed as if being numeric).
More settings can be found in the default configuration file and minimal configuration file.

You find the configuration docs on the advanced usage page here

Example

profile = df.profile_report(
    title="Pandas Profiling Report", plot={"histogram": {"bins": 8}}
)
profile.to_file("output.html")
