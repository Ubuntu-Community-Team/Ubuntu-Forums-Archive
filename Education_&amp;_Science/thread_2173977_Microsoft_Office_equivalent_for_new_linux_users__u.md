---
title: "Microsoft Office equivalent for new linux users  using zorin, elementary"
date: 2013-09-12
forum: Education &amp; Science
---

### Post by vinsoloster on 2013-09-12
I have tried wine 1.5 to install ms office , but got to know about kings office .I deal with new users of linux in educational setting . My only problem is it lacks Ms access.

---

### Post by erasmusp on 2013-09-12
Have you tried LibreOffice? It should already be installed with your Linux installation and it includes LibreOffice Base, a data base program.

---

### Post by goinglinux on 2013-09-12
> **vinsoloster said:**
> Ms access.

LibreOffice has equivalents for all of the standard MS Office applications -- and can open and save to the MS formats, too!
Word Processor = Writer
Spreadsheets = Calc
Presentations = Impress
Database = Base
and more...

Here is a link, but you should not have to install it. Erasmusp is correct, Zorin should already have LibreOffice installed. 
[http://www.libreoffice.org/](http://www.libreoffice.org/)

---

### Post by SeijiSensei on 2013-10-11
I find OpenOffice Base to be rather clunky compared to Access.  I have a Win7 virtual machine using VirtualBox that I use to run Access when I need a graphical database interface.  Most of the time I just type commands into a client like psql, but sometimes it is easier to talk to my PostgreSQL databases with Access via an ODBC connection.

---

### Post by Lars Noodén on 2013-10-12
For simple databases, Kexi should be quite useful.  It's not part of LibreOffice and must be added separately but I have seen people use it effectively.

---

### Post by ian-weisser on 2013-10-12
> **vinsoloster said:**
> My only problem is it lacks Ms access.

If you need to create new databases, Linux has lots of possibilities.

However, if you need to use existing Access databases, then you may be out of luck. Microsoft deliberately made Access databases proprietary, and has not told anyone how to read/write to them. You paid for that feature.
Several projects do have *limited* connectivity to Access databases.

---

### Post by SeijiSensei on 2013-10-14
Easysoft provides a [commercial driver]("http://www.unixodbc.org/drivers.html") for Access from Linux based on UnixODBC.  [This discussion]("http://stackoverflow.com/questions/5742322/connecting-to-access-database-from-linux") is also fairly informative.

One thing you can try with Access is separating the data tables from the queries, reports, macros, etc.  I use Access to view and mainpulate tables stored in a remote PostgreSQL database.  That makes the data available to other applications, particularly web-based ones, while providing the visual tools that assist with query design.  I have one database with a pretty complicated relational structure.  Access makes it easy to design queries.  Once you have gotten the query to do what you need, you can open the SQL command window and paste the query into something like PHP script.

---

### Post by Buntu Bunny on 2013-10-16
LibreOffice or OpenOffice would probably be closest to MS Office. As has already been mentioned, they both can read and save MS Office files (.doc, .docx) However, the metadata is not identical to MS Office, so the files will not necessarily look the same, i.e. formatting.

---

