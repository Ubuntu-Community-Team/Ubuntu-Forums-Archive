---
title: "R, ODBC, OO Base and MS Access"
date: 2010-02-09
forum: Education &amp; Science
---

### Post by asdir on 2010-02-09
I'd like to administrate a database in OpenOffice Base and be able to work with it in R. My colleague, however, insists that we have to be able to use an ODBC-connection from R (aptly called RODBC), which does not work with Base, but does with MS Access.

So I would either need a way to connect Base with R through an ODBC-connection or a way to work with MS Access databases in OpenOffice (or at least connect the database I work with in Base with a mdb-file). The latter seems to work in MS Windows, but I could not find a way in Ubuntu to register (for lack of a better word) a database ODBC driver like in Windows so that OO would list it in the "Create new Database" dialog.

So, does anyone here know
1.: **How to connect Base with R through ODBC or the like**
or
2.: **How to connect an mdb-database-file with a Base database?**

A wink in the right direction would also help a great deal, I'm really lost here.

Thanks guys.


Edit: By the way, this is how far I have come with connecting a MS Access database to OO-Base: [http://wiki.services.openoffice.org/wiki/Connecting_to_Microsoft_Access](http://wiki.services.openoffice.org/wiki/Connecting_to_Microsoft_Access)

---

### Post by gunksta on 2010-02-10
MS Access -- It is a real PITA to deal with on the Linux platform. In my experience, your best bet is to install Wine (or Cross Over) and install Access. AFAIK, you can not connect OpenOffice.org to an Access database on the Linux platform. It only works on Windows because the ODBC system on Windows will allow non-Access clients to get the data in an Access file.  While OpenOffice.org can see the numbers and the queries, it an not use forms, etc. designed for Access and queries written in OpenOffice are not saved to the Access file.

In contrast, there are several options to connect R to Base. By default, Base uses HSQLDB as it's embedded database system. If you install an independent version of HSQLDB, you should be able to ALSO install the ODBC drivers for HSQLDB and thus connect R to the file, although not to Base directly (although I think the distinction will be moot in this case).

Or, you could set up a real database -- like Postgres -- and connect to the Postgres database via Base and via R. R has a native connection to Postgres that works well and you can use ODBC if you are stubborn. OpenOffice has an extension in the repositories to make it easier to connect it to Postgres. You could use MySQL too if that is your preference.

It may be possible for Access to run as a front-end on a postgres/mysql database, which could make the cross-platform stuff easier but I'm really not sure if/how. I know it can run as a front-end to SQL Server, so it may be possible to connect an Access file to a "real" database system via Window's ODBC.

---

### Post by asdir on 2010-02-10
Thanks for the answer, if only for confirming my point of view: If I do what I want to do, there is no easy way.

I decided to go with a MySQL-Server that is accessed by my colleague's MS Access and my own OO Base. At least then we have the advantage of having the database available everytime and everywhere. Connecting MySQL with R should be straight forward.

If setting up a server (the whole thing, not just the MySQL-Server) becomes too cumbersome, I will probably go with virtualizing WinXP and installing Access there. Using Wine does not seem to work too well with Access. Go figure.

Those two seem to be the only feasible ways. It's a shame.

---

