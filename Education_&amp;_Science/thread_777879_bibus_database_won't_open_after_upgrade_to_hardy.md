---
title: "bibus database won't open after upgrade to hardy"
date: 2008-05-01
forum: Education &amp; Science
---

### Post by grw on 2008-05-01
Hi,

I have just upgraded to Hardy, but I can't get my old bibus database to open. Bibus will create a new database for me, no problem. But when I use the first connection wizard to direct bibus to the database I have been using up until now, bibus just hangs. Nothing ever opens.

I thought there might have been a problem with "LD_LIBRARY_PATH" as in Gutsy, and so I tried following the sourceforge instructions for fixing that. But it didn't work.

Does anyone have any ideas?
 Thanks
gwyn

---

### Post by plvera on 2008-05-01
Gwyn:

I have a similar problem using a database & Hardy. I created this database under windows and it works fine, but Bibus will not open it under Hardy. 

Like you, I can create a new database, but not open the existing one.

I posted a message in the Bibus forum but have not had any replies yet. 

I'll share with you what they have to say (if anything). It's very frustrating. I suppose I could reconvert the database from Endnote to Ubuntu Bibus but I would like to see this problem fixed.

Best of luck.

Pedro

---

### Post by machoo02 on 2008-05-01
What kind of database do you have: MySQL, or SQLite?  If the latter, do you have the python-pysqlite2 package installed?

---

### Post by plvera on 2008-05-01
Machoo:

I have an SQlite database. I do have python-pysqlite2 (2.4.0-2build1) installed. Synaptic manager also shows python-pysqlite (1.0.1-7) installed.

Could this be the problem? 2 version of pysqlite. If so, should I remove the older version? I'm not sure if any other program is using it.

Thanks for your help.

---

### Post by machoo02 on 2008-05-01
You could try getting rid of the older package, and see what happens.

---

### Post by plvera on 2008-05-01
Hi Machoo:

I got rid of psqlite (the older pkg) and rebooted the machine. Ran the First connection wizard and even then did the connect manually after that. However, Bibus is still not opening the file.

---

### Post by machoo02 on 2008-05-01
Would you mind attaching your library file (or sending it to me in a PM), and I'll try to see if I can open it?

---

### Post by plvera on 2008-05-04
Hello:

I figured out what the problem was. Bibus was placing all the references in the Trash folder. This also happened if I created a database in Ubuntu and moved it to windows. So, I just moved them into the References folder and Bibus is working fine.

I'll post a note in the Bibus sourceforge forum so that perhaps the developer can address this issue.

---

### Post by grw on 2008-05-04
Hi,

Yes, I found the same thing over the weekend. This is what happendd:

I entered the location of my database in the First Connection Wizard.

After several minutes trying to open my original database, I got a message saying 'dbBib.getRoot:('database is locked',)'.

While struggling with my original, Bibus had created a duplicate database but with a new name (in the .bibus folder, which is not where my datbase was stored).

All my references were in the Trash of the duplicate and I just transfered them to teh References folder.

Everything seems to work fine, if a bit slow. I am not sure if the old 'key' information has been retained though.

PS I don't have python-pysqlite2 (2.4.0-2build1) installed, only python-pysqlite (1.0.1-7)

---

### Post by appultaart on 2008-05-13
Hi,


I observed the same problem (upgrade from Gutsy to Hardy 8.04; Bibus could not open existing sqlite db, but could create new ones). When connecting to my old db I received an error message telling me that "...database is encrypted or is not a database" when I connected to my db file. 

Contrary to grw's post, I did need to install the python-pysqlite2 package (2.4.0-2build1, from Ubuntu repositories). (I have both pysqlite/1.0.1-7 and pysqlite2/2.4.0 installed). After install, Bibus is fully functional and able to open my existing database files.

---

