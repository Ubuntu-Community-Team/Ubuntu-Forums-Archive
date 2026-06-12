---
title: "Simple database"
date: 2008-12-17
forum: Education &amp; Science
---

### Post by samden on 2008-12-17
I deal with moderately-sized data sets that get very time-consuming to deal with in a spreadsheet. Usually I do some very basic manipulation in a spreadsheet, then import the data into R and manipulate them there. However I am now dealing with a dataset that will take a lot of manual editing wherever I put it, and it would be great to be able to load it into a basic relational database with a simple GUI.

Does anyone use relational databases for scientific data? What application would you recommend?

---

### Post by damis648 on 2008-12-17
Maybe Glom?

---

### Post by ahmatti on 2008-12-18
I use MySQL database for my larger data sets so I can conveniently load only selected parts to R. I use a combination of shell, gawk and perl scripts to parse and upload data to the database and R with RODBC package to query and analyze the data. No GUI there if that was you were hoping for.. 

 For instance I have some continuos measurements that are automatically uploaded to the database as cron job and another cron job runs an analysis R script that creates some plots of the data from previous days and e-mails me the figs so I can check that everything is working when I come to work in the morning. Or from my mobile if I'm out of office.

BTW. I put statistical program to the poll since I mainly use R for analysing the data, but actually I mainly store it in text files...

---

### Post by samden on 2008-12-18
Long term that sounds the best way of doing it ahmatti. But it sounds like it would take me a long time to set up and learn, time I don't actually have right now, which is why I am looking for something with a simple GUI. Once getting used to databases with that I may move to MySQL or something similar in future, but I'd rather not take too big a leap into the unknown at once!

Glom looks interesting, I have downloaded the current version but will attempt to get the latest one from source, as the latest one can apparantly import .csv files, which would make my job a lot faster. I'll have to play more once I've got it to work out if it will do the job.

---

### Post by samden on 2008-12-20
Glom does look great, but I am having difficulties building the latest version, which I would need to import my data as .csv files. So I'll be using OO.org Base for now. But I'm keeping an eye on Glom, I'd say it has a great future. Far more user-friendly than Base.

---

