---
title: "Office database"
date: 2009-05-25
forum: General Help
---

### Post by Phil Binner on 2009-05-25
I downloaded openoffice.org database to use access databases from windows. This app does not seem to be able to open a .mdb file though. Am I just doing it wrong, or is there something else I need.

Thanks in advance

Phil B

---

### Post by AFarris01 on 2009-06-13
Sorry, but OpenOffice doesn't offer native support for opening .mdb files.

I believe there is a way to access them anyway by somehow acquiring the JET runtime (MS Access' database engine) and linking the database or something, but it's been forever since I cared about trying to do this, so I dont remember how to do it...sorry :(

alternatively, there is an application available from the repositories called "MDB Viewer" which appears to allow you the ability to at least VIEW your database... you can then use this tool to export parts of the database for use elsewhere.  You could, in theory, use that tool to reconstruct the database as an OpenOffice database (.odb i believe), provided you don't at any point need to access it from MS Office.

If neither of these works for you, then I'm sorry to say it, but you're out of luck, unless you can get access to a copy of MS Office, or if Google proves me wrong one of these days.

Hope that Helps!

---

### Post by raisinglinux on 2009-06-13
What OS are you using?
 
If you can get on a Windows pc, have a look at this wiki [http://wiki.services.openoffice.org/wiki/Connecting_to_Microsoft_Access](http://wiki.services.openoffice.org/wiki/Connecting_to_Microsoft_Access)
 
Good luck...
 
-----------------------------------------
[Raising Linux . com BLOG]("http://raisinglinux.com")

---

### Post by jenkinbr on 2009-06-13
> **raisinglinux said:**
> What OS are you using?
 
If Windows, have a look at this wiki [http://wiki.services.openoffice.org/wiki/Connecting_to_Microsoft_Access](http://wiki.services.openoffice.org/wiki/Connecting_to_Microsoft_Access)
 
Good luck...
 
-----------------------------------------
[Raising Linux . com BLOG]("http://raisinglinux.com")
Let me take a wild guess: Ubuntu 8.10 Intrepid Ibex?

(taken from the OP's info)

---

### Post by raisinglinux on 2009-06-13
Yes - I see...that is why I modified my post...anyway, here is another link...I did not read in full but since you need to solution, you can read it :-)
 
[http://dba.openoffice.org/drivers/mdb/index.html#intro](http://dba.openoffice.org/drivers/mdb/index.html#intro)
 
-----------------------------
Raising Linux . com BLOG

---

### Post by ad_267 on 2009-06-13
I recently had to convert an mdb database to OpenOffice. You can download mdbtools-gmdb and then because of this bug: [https://bugs.launchpad.net/ubuntu/+source/mdbtools/+bug/369110](https://bugs.launchpad.net/ubuntu/+source/mdbtools/+bug/369110) you have to replace the executable with the one from the debian package as explained on the bug page. Then you can convert the mdb database to a csv file using gmdb2. After that you can open the csv file with OpenOffice Calc, select all the data and paste it into the OpenOffice Base Tables window to create a new table.

---

### Post by QIII on 2009-06-13
Just out of curiosity . . .

For me, thank <insert diety of choice here>, my days of creating and maintaining Access databases for clients are well behind me.

I've always wondered, though, if OOo has any way to handle the VBA code (I think I'm going to barf just saying that) that is in all of those modules you have to create to do any really useful stuff with Access other than using it as a repository.

Just an academic question...

---

### Post by ad_267 on 2009-06-13
OpenOffice can't run MS Office VBA, but it has it's own StarOffice Basic which is similar.

---

### Post by QIII on 2009-06-13
Yes, but ...

You'd have to rewrite all the code, I assume.

---

### Post by ad_267 on 2009-06-13
Yeah. The database I converted was a pretty simple and small one that didn't use any VBA. I can imagine it wouldn't be fun trying to convert one that did. I've never really used MS Access much though, but OO.o Base seems to be able to do enough without the use of code for basic use.

---

### Post by ugm6hr on 2009-06-13
I have converted my previous Access database to OO.org.

However, I did it by copying the tables into Excel, importing into Calc, and then again into Base.

I then had to rewrite all the datatbase functions from Base.

Not easy...  But I think the only way.

Details here: [http://cardiologylogbook.wordpress.com/](http://cardiologylogbook.wordpress.com/)

---

### Post by QIII on 2009-06-13
Yes, but ...

You'd have to rewrite all the code, I assume.

(BTW -- I recognize that OOo won't run MS VBA.  Hence, the question.)

(Strange -- I thought I was editing a previous post, but ended up making a new one.  It's either the bifocals or my keyboard.  I never make mistakes!)

---

### Post by carusoswi on 2009-06-13
> **QIII said:**
> Just out of curiosity . . .

For me, thank <insert diety of choice here>, my days of creating and maintaining Access databases for clients are well behind me.

I've always wondered, though, if OOo has any way to handle the VBA code (I think I'm going to barf just saying that) that is in all of those modules you have to create to do any really useful stuff with Access other than using it as a repository.

Just an academic question...

I wouldn't mind putting Access behind me, either, but OO isn't ready for prime time, IMO.  There are too many things that it doesn't have - data integrity rules is one biggie for me.

Some of the things I can't do are just because they are done differently in OO - so that's just a learning process that I will complete one day, but other features are simply missing - but, I'm guessing that's a development process that will also be completed one day.

Caruso

---

