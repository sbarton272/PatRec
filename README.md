PatRec
======

Pattern Recognition Project 18794

Parameters to Run
=================
			weights				knnK	numPrincipalComp
Baseline	[0, 0, 1]			10 		10
Vary W		[1, 0, 0]			10 		10
			[.5, .5, 0]			10 		10
Vary K		[.33, .34, .33]		10 		10
			[.33, .34, .33]		20 		10
			[.33, .34, .33]		30 		10
Vary PCA	[.33, .34, .33]		10 		20
			[.33, .34, .33]		20 		20
			[.33, .34, .33]		30 		20

F did these
-----------
Vary K		[.33, .34, .33]		3 		15  MSE: 0.56066988099698434
			[.33, .34, .33]		5 		15  MSE: 0.59321161440581149
			[.33, .34, .33]		7 		15  MSE: 0.60502767520539036
			[.33, .34, .33]		11 		15  MSE: 0.64640120750545071
Vary PCA	[.33, .34, .33]		3 		30 	MSE: 0.52245159472490155 - could overfit
			[.33, .34, .33]		5 		30  MSE: 0.57759472800056666
			[.33, .34, .33]		7 		30  MSE: 0.61106630928843075
			[.33, .34, .33]		11 		30  MSE: 0.65844050211241378

Basic Outline
=============

1) Data filtering and selection
	- Pull out the relevant users
	- Generate likeness factor (attractionFactor, digItFactor?)
2) Determine similar users
3) Predict establishment likeness factor for user
4) Recommend an establishment for the specified user

Current JSON Data
=================
- Extracted elite users into _user_reduced_elite__training.json (20054 users) -- Can be used to train characterizing user models
- Extracted all restaurants into _business_reduced_restaurants.json (14303 restaurants)
- Extracted set of sample users (non-elite) into _user_reduced_sample__test.json (2014 users) -- Can be used for testing
- Extracted top 50 reviewers into _user_reduced_top50.json

TODO v2.0
=========
- (UPDATED -- see below) Get user vector with restaurant types
- (DONE) Expand restaurant information with Price Range, Geograpich Information, Average stars (Baseline/Restaurant Prior) -- REMARK: Added to new file .._mapping_ext.csv for visual validation with old file -- Difference: Switched user_id and business_id columns while still sorted by restaurants
- (DONE) Predict Rating -> Only for selected user
- (DONE) Add prediction baseline where predicted user rating is just restaurant avg
- (DONE) Clean-up validation code
- (DONE) Incorporate PCA
- (DONE) Move knn and pca to a similar user class
- Analysis for report: Best K, Best User Features
- Add restuarant data to recommendation

Secondary goals:
================
- DigIt factor (norm. star=star/avg.star)
- Recommendation filter for nearby restaurants
- Implement further intelligent clustering/classification scheme with K-Means/Naïve Bayes/GMM..

Get user vector with restaurant types
=====================================
- The user_feature_matrix script has been updated with current progress
- A description explains the issues involved
- Pseudo-code added as an example demonstration of how the user vectors could be assembled
