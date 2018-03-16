You can find the following three items within this folder:
#1. wiki_input.tsv
#2. output folder
#3. labeled_output folder

=====================
#1. wiki_input.tsv
=====================
The wiki_input.tsv contains 100K Wikipedia table columns that we randomly sampled from a recent crawl of Wikipedia tables (note that since Wikipedia pages are constantly being updated, the tables we crawled may not always match the most recent version available online). We ran different error detection algorithms using this data set to produce top-1000 results for each method, and manually label predicted errors to assess result quality. 

Each row in the file corresponds to an input Wikipedia table column. There are a total of 6 attributes in the file:
	A1: the URL of the Wikipedia page from which the table was extracted
	A2: the caption of the whole table (note that this is empty for most tables)
	A3: the heading of the section from which the table was extracted
	A4: a 0-based column id (count from the left)
	A5: table meta-data, such as the column header
	A6: values in the column, connected by "___"


=====================
#2. output
=====================
The output folder contains output files for 11 methods compared in the Auto-Detect paper. Each file is named as "wiki_pooling_X.tsv", where X is the name of the method.

Each file contains 8 attributes. The first 6 attributes are the same as the input file, and the last 2 attributes are:
	A7: the pair of values in the comlumn regarded as the most incompatible
	A8: an algorithm-specific compatibility score

=====================
#3. labeled_output
=====================
The labeled_output folder contains the sampled output files for 11 methods compared in the Auto-Detect paper. Each file is named as "wiki_pooling_X_Y_Z.tsv", where X is the name of the method compared, Y and Z denotes the range from which 100 predictions were sampled in top-1000 for manual labeling.
For example, wiki_pooling_Auto-Detect_200_500.tsv contains 100 values sampled from top-200 to top-500 of Auto-Detect.

Each file contains 9 attributes. The first 8 attributes are the same as the output file, and the attribute is:
	A9: a manual label, where a label of 0 means the pair of values discovered is judged as compatible, and a label of 2 means the pair is judged as incompatible. A label of 1 means the case is a bit ambiguous and the labeler cannot judge for sure. Such cases will be ignored and will not affect quality results reported.

	
The detailed setting of the 11 compared methods can be found in our paper. Followings are the pointers to each method:
F-Regex: "Supported Data Types, Trifacta Reference", https://docs.trifacta.com/display/PE/Supported+Data+Types
PWheel: "Potter's Wheel: An Interactive Data Cleaning System", http://control.cs.berkeley.edu/pwheel-vldb.pdf
dBoost: "Outlier Detection in Heterogeneous Datasets using Automatic Tuple Expansion",  https://dspace.mit.edu/bitstream/handle/1721.1/101150/MIT-CSAIL-TR-2016-002.pdf?sequence=1
Linear and LinearP: "A linear method for deviation detection in large databases", https://www.aaai.org/Papers/KDD/1996/KDD96-027.pdf
CDM: "Towards Parameter-Free Data Mining", http://www.cs.ucr.edu/~eamonn/SIGKDD_2004_long.pdf
LSA: "An Optimization Model for Outlier Detection in Categorical Data", https://arxiv.org/ftp/cs/papers/0503/0503081.pdf
SVDD: "Support Vector Data Description", http://citeseerx.ist.psu.edu/viewdoc/download?doi=10.1.1.100.1425&rep=rep1&type=pdf
DBOD: "Algorithms for mining distance-based outliers in large datasets", http://www.vldb.org/conf/1998/p392.pdf
LOF: "LOF: Identifying Density-Based Local Outliers", http://www.dbs.ifi.lmu.de/Publikationen/Papers/LOF.pdf
Auto-Detect: see our paper.
