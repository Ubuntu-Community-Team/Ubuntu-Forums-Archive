---
title: "AS/400 Database Connections"
date: 2009-03-23
forum: General Help
---

### Post by parmstrong on 2009-03-23
I work for a small ISP.  I need some help connecting to an AS/400 to query customer information.

I am fairly well versed in administering/programming : Mysql, PHP, Perl, Apache, MTA's, etc...but this problem continues to elude me.

Under normal conditions, to access this db we use a windoze machine, "ASNA Acceler8db" and a proprietary VB application to interface with it.  I am trying to find an alternative way around this, "OPEN SOURCE", and build some web gui's.

Ultimately I would like to connect via PHP.  Immediately, I would be satisfied to get any app on my Ubuntu machine to connect to it; Open Office Spreadsheet or Base even...just to see that it can be done.

I have done a lot of Googling and followed previous threads to no avail. Has anyone accomplished this before?  Where is a good starting point ?  Thanks!

---

### Post by parmstrong on 2009-03-24
bump

---

### Post by parmstrong on 2009-03-26
bump.

---

### Post by Zimmer on 2009-03-26
When I last had to query data in an AS/400 we had no PC interface (and the IT dept. were never happy with me suggesting one!) so I arranged queries on the 400 to create flat subset files which I then imported into a PC environment for analysis.
( I used PC SAS for that, but it depends on how much data you have and what you want to do with it...)
Not quite the solution you asked for, but just my 2 cents... in case it helps you decide a different route..

---

### Post by parmstrong on 2009-03-27
I wish I knew more about "AS/400".  In Googling around it sounds like it's a popular business db solution, but to me it looks like an archaic POS.  The UI is an ugly green screen and even after logging in locally I have no idea how to extract anything from it.  

As stated in the original post it would be a step forward if I could at least figure out how to set up OO Base or ANYTHING to interface with the box.  I do appreciate the response but I would have no idea how to go about accomplishing what you described.

---

### Post by Zimmer on 2009-03-28
[http://www.scribd.com/doc/2511124/Query-400](http://www.scribd.com/doc/2511124/Query-400)

May help you use QUERY on the AS400. It was easy (as I remember it! back pre 1995 when I moved on to VAX and RECITAL DB's ) but I cannot find any notes I may have made which suggests it was very simple to access and use. I do remember getting confused initially over the jargon and Libraries, submitting batch jobs to the Queue which were new concepts to me at that time etc.. but  at a glance looks like the link above has the manual.
Other links you may want to follow up are..

[http://as400blog.blogspot.com/](http://as400blog.blogspot.com/)
[http://www.as400pro.com/tipView.php?cat=WinAS400&key=4472](http://www.as400pro.com/tipView.php?cat=WinAS400&key=4472)
[http://itknowledgeexchange.techtarget.com/itanswers/subtotal-and-average/#answer](http://itknowledgeexchange.techtarget.com/itanswers/subtotal-and-average/#answer)

PS.
It may be possible to link OO database directly to the flat files( there may be options in QUERY to create other DB formats) you create and create a report structure that does not impact 'live' data processing on the AS400. I am unable to confirm or test this as I took early retirement 5 years ago so have no access to  an AS400 :(

---

### Post by parmstrong on 2009-03-30
Again, thanks for the reply.  The manual will certainly give me something to chew on.  The concepts are definitely foreign.  From what I gather, pulling out data and (ultimately) modifying it outside of the proprietary software we have been sold is not probable, at least for my level of programming.

---

### Post by Zimmer on 2009-03-31
As a rough guide, the flat text files produced by QUERY can be imported to OO spreadsheet. Open and select file type as CSV (even though the file is not comma separated) this will open the text import dialog which allows you to specify the columns to import.... try OO with a .txt file with some text in it , anything really, just to see the import dialog and how to manipulate it... select the fixed width option and dynamically select the column widths and alter the column formats.

It is also possible to create macros of this process, which would speed up a weekly import of data to a report....

---

### Post by davidfree007 on 2009-04-28
Did you get to the bottom of this?

What are you looking to connect to the as400 from? Windows? Linux?

The database on the as400 is a standard relational database similar to db2 and oracle. 

The easiest way to get at the data would be to use java and the jdbc driver available in jt400.jar. Then it would just be a case of getting the right host name and parameters to connect to the as400.

If you cant use java directly you may still be able to use the driver using a odbc-jdbc bridge. 

The other option is to install the ODBC driver onto your php box. I suspect this option is only available for windows. ODBC driver is part of a product called client access, if your client has as400 he should be aware of this product. Once client access odbc driver is installed you can make a standard odbc connection from php

give me a shout if you have any more questions

---

