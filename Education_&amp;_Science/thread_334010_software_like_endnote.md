---
title: "software like endnote"
date: 2007-01-08
forum: Education &amp; Science
---

### Post by cuonght on 2007-01-08
I am new user of ubuntu, so could someone help me, please?
Is there any endnote - like software for Ubuntu? And how can I convert my library in endnote to this new software?

---

### Post by WebDrake on 2007-01-08
> **cuonght said:**
> I am new user of ubuntu, so could someone help me, please?
Is there any endnote - like software for Ubuntu? And how can I convert my library in endnote to this new software?
You mean the reference database software (made by the same people who make Reference Manager) that integrates with Word so you can enter references, captions, etc. in given journal formats?

OpenOffice.org aims to have similar functionality built-in but the present version is pretty basic compared to what Endnote/RefMan can do.  See [http://bibliographic.openoffice.org/](http://bibliographic.openoffice.org/) which details the timeline for the development of this service into a serious contender.

In the meantime, there are also some third-party creations.  You might want to look at,
[http://en.wikipedia.org/wiki/Category:Free_reference_management_software](http://en.wikipedia.org/wiki/Category:Free_reference_management_software)

Bibus is supposed to do something similar to Endnote, but I don't have personal experience.  See: [http://bibus-biblio.sourceforge.net/](http://bibus-biblio.sourceforge.net/) and [https://wiki.ubuntu.com/Bibus](https://wiki.ubuntu.com/Bibus) although I'm not sure the Ubuntu wiki page is up to date.  I don't think Bibus is in any of the Ubuntu repositories at the moment but I doubt it's too difficult to install.  An advantage is that Bibus apparently works with MS Word as well, so databases should be transferable between you and less-enlightened colleagues. :)

If you have to, I suppose it might be possible to run MS Word and Endnote together under Wine.  Check out the Wine project's compatibility list to see if this is a possibility.

---

### Post by cuonght on 2007-01-08
Thanks for your information

---

### Post by machoo02 on 2007-01-09
> **WebDrake said:**
> 

If you have to, I suppose it might be possible to run MS Word and Endnote together under Wine.  Check out the Wine project's compatibility list to see if this is a possibility.

FWIW...I've attempted to do this using CrossOver, but to no avail.  Both Word and Endnote will work fairly well, but trying to use CWYW functionality in Word causes it to tank on opening.  I haven't tried this with regular WINE because I've never been able to get Office to install properly... ](*,)

I've been using Bibus for a little while, and been fairly pleased with the results.  The instructions on the Bibus site are pretty straightforward for installation/integration with OO.o/importing references from Endnote.

[_This page_]("http://wiki.services.openoffice.org/wiki/Bibliographic_Software_and_Standards_Information") from the OO.o wiki has a list of a number of different bibliographic softwares both open and closed source.

---

### Post by Mr Al on 2007-01-10
This recently came up in this forum:

[http://www.ubuntuforums.org/showthread.php?t=327675]("http://www.ubuntuforums.org/showthread.php?t=327675")

---

### Post by ecastro on 2007-01-11
There are plenty of bibliographic applications for linux. Try PyBibliographer, BibTex, sixpack etc.

But my favourite replacement for endnote is **Bibus** 
[http://bibus-biblio.sourceforge.net/wiki/index.php/Main_Page](http://bibus-biblio.sourceforge.net/wiki/index.php/Main_Page)

This applications works as an stansalone bibliographic database, connects to internet sources for searching, makes final bibliography styling and formatting  AND integrates with OpenOffice (and other tool, even MS-Word) to on-the -fly citation. 

Bibus is on standard repos, I think.
Bibus site offers more up to date versions as Ubuntu .deb packages: easiest instalation

---

### Post by akniss on 2007-01-11
Add the following repositories to your /etc/apt/sources.list:

```
deb http://switch.dl.sourceforge.net/sourceforge/bibus-biblio ./
deb-src http://switch.dl.sourceforge.net/sourceforge/bibus-biblio ./
```

Then run:
```
sudo aptitude update
sudo aptitude install python-pysqlite2 bibus bibus-doc-en
sudo aptitude install mysql-server mysql-common mysql-client python-mysqldb
```

You should then be able to start up bibus and get the first connection wizard.  I wrote my PhD dissertation using bibus/OOo and had very few issues.  I highly recommend it.

---

### Post by nike984 on 2007-01-14
There is a document management software named '[jLibrary]("http://jlibrary.sourceforge.net/index.html")'.
It is built based on java, so I think it will also work on Linux.
If your using Mac, there is a great application, 'DevonThink',
otherwise than that jLibrary seems to be a promising app.

---

### Post by WebDrake on 2007-01-16
> **akniss said:**
> Add the following repositories to your /etc/apt/sources.list:

You should then be able to start up bibus and get the first connection wizard.  I wrote my PhD dissertation using bibus/OOo and had very few issues.  I highly recommend it.
Mmm, I must check it out.

Since people have mentioned BibTeX I should add that this is in some respects a fantastic solution (and for people like me who use LaTeX it's essential), simple to use, but tricky if you want to customise it.  Fortunately a lot of work has already been done for you by wonderful dedicated people, making it in many ways the most powerful bibliographic solution available.

---

### Post by DrOlaf on 2007-01-23
No-one in this thread has mentioned [JabRef]("http://jabref.sourceforge.net/") yet, so I will. It's a Java app that allows you to maintain your BibTeX library, but also has more EndNote-like features like the ability to search online libraries such as Medline. I use it with my BibTeX libraries and I think it's great.

---

### Post by PacShady on 2007-05-08
Is it just me, or has anyone else noticed that, at least with the version of OpenOffice in feisty, that it is EXTREMELY UNSTABLE to the point where it crashes if it so much as LOOKS at a macro like Bibus or even it's own Dictionary tool? I'm trying to install a version of official OpenOffice I've got lying around (ie. not an Ubuntufied version) to see if it's more stable. But has anyone else got around this issue?

'Shady

---

