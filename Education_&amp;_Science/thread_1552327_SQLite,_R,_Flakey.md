---
title: "SQLite, R, Flakey"
date: 2010-08-13
forum: Education &amp; Science
---

### Post by gunksta on 2010-08-13
Curious to see if anyone else has experienced this -- In the past, I have used Postgres for projects with large data sets. In the last few months I have become interested in using SQLite for data management, because it relieves of me of needing to run a full RDBMS (either locally or on a separate machine).

Recently I got a project which seemed perfect for SQLite. I needed to run some regressions against several years worth of data files, all saved in SPSS' .sav format. So, I imported them into R (each file is 300+ wide at ~75,000 rows) and made each file into a separate table. Sadly the data structure changed with each year and it's a PITA managing all of the changes. That's one of the reasons I wanted it in a DB. I have defined a set of views which make my life much easier and let R work with the subsets of the data that I am actually interested in.

But, I have noticed that R + SQLite seems a little flakey. I have gotten some weird table locked errors when trying to write my data into the SQLite file. To get the table write functions to work, I sometimes have to exit my R process, make sure I have closed SQLiteman and start all over. Once or twice I have even succeeded in freezing EMACS.

Anyone else ever experienced anything like this? It doesn't seem to happen when I work with Postgres. It could be R+SQLite or it could be me doing something dumb to SQLite. I'm not really sure ATM.

Thought?

---

### Post by gunksta on 2010-08-13
For example - I just passed a perfectly valid request to the file. I have used this syntax numerous times in the past few days and I know it is correct. EMACS, R and SQLite have been spinning uselessly for more than a minute. It's really annoying. This should only take a couple of seconds. At least, that's all it took the last time it ran successfully.

I guess I should test this and see if my problem is EMACS or R+SQLite.

---

### Post by gunksta on 2010-08-13
This is ridiculous. Here's what I do (simplified).


[LIST=1]
[*]Open a connection to SQLite.
[*]Make a data request.
[*]Play with the data.
[*]Take my new dataframe and try to write it back to SQLite as a NEW table. I am not over-writing anything. I want it as a new table.
[/LIST]
Step 4 hangs unless I stop the R process within EMACS.

Will test this without EMACS to see if I observe the same problem but I am beginning to suspect it has something to do with how R handles the SQLite connection. But, if I first close the R session and then re-open it and then re-do my connection to SQLite and then it will work. Really weird.

What's even worse, is that the failed attempts DO write something to SQLite, but I have to drop the table and redo it because I'm not sure it's all there.

---

### Post by gunksta on 2010-08-16
I am using the default sqlite3 binaries provided by Ubuntu. I didn't compile. My "application" is just a set of R scripts that dump a bunch of info into SQLite, run some SQL against the tables to clean things up and then selectively pull parts of that information back out for analysis.

In other words, it's a hodge-podge of quickly written scripts and half-baked code. It ain't enterprise quality code.

I am half wondering if my problems are in my utilization of SQLite. In the past I've done this same sort of thing with a Postgres Server and not had any real problems, but SQLite ain't Postgres and I fear I may be doing something that SQLite doesn't handle very well or is not meant to do at all, which could be the source of these weird connection errors.

I guess I need to go over to the R-users mailing list and ask there, but the responses there are sometimes testy to say the least.

---

### Post by Axolotl9250 on 2010-08-17
I have used R and SQLite before in EMACS without much problem, normally both at the same time with ESS and the SQL mode that EMACS has, although I must admit I've only lifted things from the Database, I've not altered data in R and needed to send it back the other way yet. But then my uses are probably no where near as complex as yours.

---

### Post by gunksta on 2010-08-17
The fact that you have not experienced any of the weird connection issues that I have make me think that I am causing my own problems. I may not be disconnecting correctly.

---

