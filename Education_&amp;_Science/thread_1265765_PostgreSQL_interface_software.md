---
title: "PostgreSQL interface software"
date: 2009-09-13
forum: Education &amp; Science
---

### Post by samden on 2009-09-13
I am intending to use PostgreSQL for managing some of my data, with graphing and analysis done in R. Previously I have been using .csv files and R, but a dedicated database is probably a better choice. 

What software would be best as a simple interface to PostgreSQL? Do I need anything more advanced than the psql command-line client? If you use postgresql, what software do you manage it with?

This is my first foray into the world of databases, so any tips for a beginner would be much appreciated!

---

### Post by gunksta on 2009-09-14
Depending on the size/complexity of your data structures, I think you will find that this is a very nice combination. I tend to let the database shape my data and I use R to dig into it. More importantly, the type of data I work with is nearly always relational, which is possible to do in R, but I find it more comfortable to do in a database.

[LIST]
[*]Vim/EMACS both have nice modes/ways of interacting with databases.
[*]psql is a very nice tool. Be sure to learn it's internal functions too in addition to what postgres does. Reading the man page is a good use of time.
[*]Although I usually stick to the command-line, pgadmin3 is a very nice program and doesn't pull in a ton of weird dependencies. If you are used to Vim/EMACS, it probably won't appeal to you but I know several developers who were used to the MS database development environment and they all use pgadmin3 and seem to think it is a good replacement for the MS tools.
[*]I recommend skipping the rodbc package. ODBC is, in my opinion, a really confusing set-up under Linux. I prefer the easier to use RPostgreSQL, but it's not in the Ubuntu repos, so it breaks every time I upgrade Ubuntu.
[/LIST]

For what it's worth, here's how I tend to organize things. I will use postgres to hold/organize the data. I will then build one or more views, which correspond to the various things I want to do in R. Therefore, the SQL syntax in the .R file can be kept very simple and minimal. For example, here is the opening section of a project I did a couple of months ago showing how to use the RPostgreSQL extension.

```
# Clear out any and all old crufty numbers / data
rm(list=ls())

###################################################################################################################################
# Worker Calculations
###################################################################################################################################

# Load up all necessary libraries.
library(RPostgreSQL)


# Database connection info
localhost <- dbConnect(PostgreSQL(), user= "username", password="blahblahblah", dbname="username")

# Create worker datasets
#avg100.df <- dbGetQuery(localhost, "SELECT * from mn_timestudy.avg100w")
avg101.df <- dbGetQuery(localhost, "SELECT * from mn_timestudy.avg101w")
```

---

### Post by samden on 2009-09-14
Thanks for that gunksta, I must say that it is primarily because of you mentioning it a few times elsewhere that I have decided to try it out. I'll probably stick with psql in that case, I prefer the command line too these days. I have PGAdmin and it makes it seem more complicated rather than less!

Unfortunately I'm hitting a wall just installing RPostgreSQL:
```
2> install.packages("RPostgreSQL")
Warning in install.packages("RPostgreSQL") :
  argument 'lib' is missing: using '/home/samuel/R/i486-pc-linux-gnu-library/2.8'
trying URL 'http://cran.ms.unimelb.edu.au/src/contrib/RPostgreSQL_0.1-4.tar.gz'
Content type 'application/x-tar' length 137702 bytes (134 Kb)
opened URL
==================================================
downloaded 134 Kb

* Installing *source* package 'RPostgreSQL' ...
checking for gcc... gcc
checking for C compiler default output file name... a.out
checking whether the C compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables... 
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ISO C89... none needed
checking for pg_config... no
configure: checking for PostgreSQL header files
checking for "/libpq-fe.h"... no
configure: error: File libpq-fe.h not in ; installation may be broken.
ERROR: configuration failed for package 'RPostgreSQL'
** Removing '/home/samuel/R/i486-pc-linux-gnu-library/2.8/RPostgreSQL'

The downloaded packages are in
	/tmp/RtmpR5xJO6/downloaded_packages
Warning message:
In install.packages("RPostgreSQL") :
  installation of package 'RPostgreSQL' had non-zero exit status
```
I have tried the New Zealand and Australian archives in case there was an issue with one of them (deleting the downloaded file in between), with no luck. I can't figure out what could be wrong.

---

### Post by gunksta on 2009-09-15
Looking at the error messages, I suspect you don't have libpq-dev installed.

```
sudo apt-get install libpq-dev
```Once that finishes, try installing the plugin again. You don't need to exit from your R session unless you do so to drop back to the command-line to install libpq-dev.

As for pgadminIII - It's installed on my work computer but not on my home computer, which I also use for development. As graphical database managers go, I think it is pretty nice (although I wish queries were opened in new tabs rather than new windows) but it lacks in the text-editing department. This is rarely a problem for people converting to postgres on/from Windows, since most Windows developers have never learned the joys of letting their fingers do the walking.

For grins and giggles, I edited my original post and I've included a cheat-sheet I made a while back for psql. Since I wrote this, I have changed the formatting of my cheat sheets a little and while I need to update this file to the current standards, I do think it is reasonably clear. It's not comprehensive, but it does have the stuff that I need to use most often.

---

### Post by samden on 2009-09-15
Thanks heaps gunksta, that was the problem. I can see that cheatsheet will be very useful.

All seems to be working well for now, and once it is running properly it is simpler to use than my old stacks of .csv files. I look forward to a more organised future, until my new work computer arrives and I have to change everything...

---

### Post by gunksta on 2009-09-15
I'm glad it worked.

If you come up with a really slick way to move your work environment from one computer to another, let me know.

---

### Post by samden on 2009-09-15
I highly doubt there will be a slick way to do it, as the new computer will be running Windows (grrr, universities) and I'll have no admin rights. Although I am VERY tempted to install Ubuntu as a dual boot on it I suspect IT would get rather upset about that.

I might just do it anyway though, if nothing goes wrong they won't notice until my contract runs out and someone else needs the computer, and I might be able to remove it reasonably cleanly. 

IT departments are supposed to help you do your work, not get in the way, or so I thought... :)

---

