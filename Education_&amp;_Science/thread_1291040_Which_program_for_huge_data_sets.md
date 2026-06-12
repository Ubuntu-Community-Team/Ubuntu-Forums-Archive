---
title: "Which program for huge data sets"
date: 2009-10-14
forum: Education &amp; Science
---

### Post by asdir on 2009-10-14
For my standard data set, I use OpenOffice spreadsheets for data-cleaning and managing and R for analysis (I am an economist, by the way).

However, sometimes I just need more than ~64000 rows (observations) or more than 1024 columnes (variables).

Is there any comfortable way to manage this kind of data set? Is there maybe a simple way to use a database software with some kind of view and mathematical tools similar to OpenOffice spreadsheets?

---

### Post by dgoosens on 2009-10-14
not quite sure if it would be a viable solution, but maybe you should check out gnumeric...
[http://projects.gnome.org/gnumeric/](http://projects.gnome.org/gnumeric/)

as you can read here: [http://projects.gnome.org/gnumeric/faq.shtml#5](http://projects.gnome.org/gnumeric/faq.shtml#5)
> Does Gnumeric support more than 256 columns?
Yes. In the 1.8 series this requires a re-compile. (Edit SHEET_MAX_COLS and SHEET_MAX_ROWS in src/gnumeric.h and re-compile.) In the 1.9 series, right-click on the sheet tab and select "Resize".

I believe the Ubuntu repos only provide gnumeric 1.8.4 thus you might want to look for the 1.9 version

---

### Post by asdir on 2009-10-14
I am not so fond of compiling myself, but generally this is pretty much what I was looking for (provided I can save as csv, which I guess I can in gnumeric).

Latest stable seems to be a 1.8 release, though. And 1.9 does not have debs. :(

Still: Thanks a lot.

---

### Post by dgoosens on 2009-10-14
I'm way to nice...

if you look on this page, you'll find the 1.9 version in DEB
[http://packages.debian.org/testing/gnumeric](http://packages.debian.org/testing/gnumeric)

just pick your correct architecture (at the bottom of the page) and select the nearest FTP-location...

and yes, you can save as *.csv (*.txt)

---

### Post by asdir on 2009-10-14
> **dgoosens said:**
> I'm way too nice...

True! :)

---

### Post by gunksta on 2009-10-14
Speaking for myself, I would not want to do much data munging using a spreadsheet that has 64K rows or more than 1024 columns. That just sounds painful. I work with a lot of government data sets and I would never use a spreadsheet to store a data set of that scale.

Fortunately, there are lots and lots of options. You are obviously already familiar with/comfortable with OpenOffice.org. IIRC, the default Ubuntu/Kubuntu installation does not include the database module, but it can be easily acquired by installing the full meta-package. You can use synaptic, the package name is openoffice.org. If you like the CLI.

```

sudo apt-get install openoffice.org

```Using the database module is somewhat comparable to using Access, although Access _is_ nicer in a few ways. (God I hate admitting that.)

But, if you've used spreadsheets for this long, your data is obviously not relational (or you are a masochist), so you could consider PSPP. It is a rather nice reimplementation of SPSS. It can handle as many rows and columns as you care to throw at it. If you have used SPSS in the past, you will find that PSPP has implemented all of the data trasformation syntax and some of the basic analysis syntax. It can save output as $.sav and $.por. At this point the output from PSPP such as CrossTabs looks poor compared to a spreadsheet or R, but it's fidelity with the SPSS format seems to be very very good. I use it all the time to look at SPSS files and send people SPSS files and I've never had a problem.

```

sudo apt-get install pspp

```

As an added bonus it comes with a GUI called psppire, which you should find in a sub-menu called "Education". Because it saves the data in the .sav format, this will make it easy for you to send the dataset to anyone who uses SPSS/PSPP/R. You mentioned that you use R for your data analysis (YEAH!). You will need to use the "foreign" library to import the data from the .sav file to R.

```

sudo apt-get install r-recommended

```This will pull in several other nice packages for R. If you don't want the extra stuff . . . . . 
```

sudo apt-get install r-cran-foreign

```Once you have installed the foreign library, you can use it to read/write to several useful formats including SPSS, SAS, etc. Open R and then:
```

?base::Foreign

```will bring up the help documentation for the package. You load it with 
```

library(foreign)

```The command you will want to look at first is read.spss.
```

library(foreign)
?read.spss

```All that being said (and I guess it is quite a lot looking back at it). You could just use R to manipulate your data. It has all sorts of nice tools for doing so and will store the data in a file called .Rdata in the folder where you start R from. If none of this seems appealing you could try installing MySQL or PostgresSQL and access your data via queries from R, which is a work flow that I am utterly dependent on any more. SQLite3 may also work for you. I've never used SQLite in conjunction with R, but judging by the traffic on the R-users mailing list it is a viable and well-liked option. I intend to try it on my next project to see how well it works.

Lots and lots of options for you.

---

### Post by asdir on 2009-10-15
Thanks for all the advice (and taking out the time to actually write it down).

I am not sure if it is time efficient to learn how to cope with databases, though it seems to be one of the nicer options as long as I can find an easy way to export it to R.

(For others reading this for help, [here]("http://sheepdogguides.com/fdb/fdb1imp1.htm") is a nice tutorial on how to transfer data from spreadsheets to base.)

[PSPP]("http://www.getdeb.net/release/3411") certainly would be a nice option considering that I have a little experience with SPSS. I am not sure, though, if data manipulation will be as easy to learn (though certainly slicker) as in spreadsheets. I am impressed with the GUI, though. I would not have thought that such a small and very narrowly targeted project could come up with sth. like that.

However, if I have to learn data manipulation via CLI anyway, do you think it would be wiser to learn how to do all of it in R? Then I would actually not even need another program and would not have to bother with formats.

Anyway, thanks a lot for the advice, it's well appreciated.

---

### Post by gunksta on 2009-10-15
Given that you are dealing with flat data-sets, it is entirely possible that learning how to use R for your data transformations may very well be the simplest option.

A couple of questions:

[LIST=1]
[*]When you get the original data set, what is the data format?
[*]What type of data transformations do you need to do?
[/LIST]
This forum has several regular contributors that know R very well. Another good resource is the R-users mailing list (but read the posting guidelines first).

If you can throw out some examples of what you need to do, possibly in a new thread that includes the word R in it to get their attention, I am sure that we can help yo figure out how to do what you need to do. R is a funny language, but often very elegant once you figure out it's tricks.

The nice thing about PSPP/SPSS is the .jnl file. When you use the GUI, PSPP will save the actual syntax for the commands that you are using. The analytical tools of PSPP are not complete, but for data transformation it is complete and the because the GUI will literally teach you the syntax, it is reasonably easy to learn the syntax. I'd have to look, but I think it saves the .jnl file in the directory where the .sav/.por file is. If I'm wrong, it probably saves the file in ~. Either way it's a nice trick and one that I sincerely wish we could offer to new R users.

---

### Post by samden on 2009-10-15
If you did decide to go down the database route, R is able to directly issue SQL queries and access data from a number of databases, so getting the data to R would be no problem. I've had a play with PostgreSQL and it works great with R, but then I had to move to a Windows computer as my main work machine and couldn't continue with it unfortunately.

So I tend to do the majority of my data manipulation in R, and it works great. Just save your data in a flat .csv or tab-delimited text file and away you go. Once you get the hang of it it is far easier and quicker than using a spreadsheet.

What I really like about using the CLI for data manipulation is that you either make one really big mistake that is immediately obvious, or you manipulate it perfectly. You don't run the risk of little errors sneaking in here and there from copying and pasting stuff in spreadsheets.

---

### Post by ahmatti on 2009-10-16
> **asdir said:**
> However, if I have to learn data manipulation via CLI anyway, do you think it would be wiser to learn how to do all of it in R? Then I would actually not even need another program and would not have to bother with formats.


I thing dropping spreadsheets and only working with CLI and scripts is one of the most useful things I have ever done (I did this many years ago). R has good capabilities for manipulating data so I would recommend doing the whole thing in R. It sounds that your dataset is not too large (if you have enough memory) anyway and you can manage it with R without problems. 

I wouldn't bother with databases as long as the dataset can fit in your RAM or unless you only need to work with a subset of the data and don't want to load the whole dataset. In either of the above cases you may benefit from sqldf ([http://code.google.com/p/sqldf/](http://code.google.com/p/sqldf/)) or filehash package.

---

### Post by asdir on 2010-01-13
It turns out that the dataset will grow beyond R's capabilites. Therefore I plan switching to a database.

Of course I would create the database with OpenOffice Base.

That presents me with two problems:

**1.: Compatability with my colleague's MS Access**

Is there an easy possibility to share one database, possibly even using a server? What format do we have to choose for the database?

**2.: Import into R**

How do I import Base files into R? I could not find any clue on how to do it with RODBC (though I am not done looking for it) or any similar program. Could you point in the right direction?

Again, any answer is much appreciated.

---

### Post by earlycj5 on 2010-01-13
From my experiences, I'd set up a PostgreSQL database on the machine, use OOo as a front-end for it, and use R to access the data in the database.

I've had to do that in the past with some of my large datasets.

Doesn't solve much for MS Access compatibility though I don't think.  To be fair, I don't know Access that well.

Though that may be overkill or beyond what you want or need to do.

---

### Post by oldfred on 2010-01-13
I used to use MS Access a lot with ODBC connections. It was primarily to MS SQL server but any ODBC connection should work depending on the design of the ODBC driver.

One of many links in google:
[http://psqlodbc.projects.postgresql.org/](http://psqlodbc.projects.postgresql.org/)

Many years ago when Supercalc only could handle enough rows for two pages of greenbar paper, I converted to dBase. Then with windows95 went to MS Access and stiil have not found a good front end in linux but not using dbases a lot now that I am retired.

---

### Post by asdir on 2010-02-10
Oops, I just realised I posted (almost) the same question twice. Here is the second threat with a (bit more) conclusive answer:

[http://ubuntuforums.org/showthread.php?t=1402446](http://ubuntuforums.org/showthread.php?t=1402446)

---

### Post by epigram on 2010-02-11
Why kind of analysis are you doing btw?  It seems that you could most likely reduce the column space fairly easily depending on your application.

Cheers,

Jonathan

---

### Post by nevaeh.aaric on 2010-02-12
I am not sure if it is time efficient to learn how to cope with databases, 
though it seems to be one of the nicer options as long 
as I can find an easy way to export it.

---

