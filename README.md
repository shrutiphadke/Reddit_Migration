# Reddit_Migration
Descriptive analysis of precursors of high level activity on r/conspiracy subreddit on reddit
This repository contains jupyter notebooks describing how every feature was calculated and also contains the classification model notebook containing feature selection

Data Preprocessing steps
The data that was used was the reddit_comments and reddit_posts data sets available on Google BigQuery. The data reddit data was pre-processed in the following format:

We filtered the entire data to people who have commented in the /r/Conspiracy atleast 10 times every month. [We arbitrarily decided on 10 as we deemed a minimal activity was required for analysis]
We truncated the focus of our analysis to January 2016 to December 2017.[NOTE: The data considered is not restricted to this timeline, only our focus for analysis is. This will be further explained later]
We eliminated all users who posted or commented on reddit for the first time before 2010. [The timeline was arbitrarily selected to limit the data handeled. This filtered eliminated approx. 150 users]
Based on percentile measures we categorised the users into two different classes of interest.
Users whose frequency of posting and/or commenting was in the top 75 percentile of each month - High Activity Users
Users whose frequency of posting and/or commenting was in the top 25 percentile of each month - Low Activity Users
We ranked the high activity regions lower bounds and found the least of them to be 36 post+comments in a month. We eliminated all users who have posted more or equal to 36 before our interest period i.e. January 2016. This helped us claim that we have high-activity users formed in our interest period.
We selected users for each month when they first cross the threshold to become high-activity users. All the activity of these users from the time of their birth on reddit i.e. first post or comment, was then added to the high.csv.
We selected unique users for each month i.e. if a user appeared in the high-activity user region in one month then he or she will not appear in the next irrespective of whether their activity was in the high-activity or low-activity region.
We selected random unique users who are in the low-activity region during the month of consideration. We used their activity from birth to month of consideration to populate low.csv. [NOTE: We followed the same unique principle for the low-activity dataset as well.]
Finally, we appended these datasets with all possible features transformations in terms of means, maximum values, minimum values, standard deviations.
SCHEMA:
author
num_archived_comm
num_subs
min_score
max_score
avg_score
num_contra_comm
num_gilded_comm
num_distinguished_comm
num_comments
consp_comm
month_active_comm
avg_len_comm
num_archived_posts
num_subs_posts
min_score_posts
max_score_posts
avg_score_posts
min_replies
max_replies
avg_replies
num_gilded_posts
num_distinguished_posts
num_posts
month_active_posts
consp_posts
num_stickied_posts
num_over18_posts
avg_postlen
