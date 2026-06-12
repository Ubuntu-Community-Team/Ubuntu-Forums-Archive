---
title: "Question about running kingsoft office in ubuntu using wine"
date: 2009-05-27
forum: General Help
---

### Post by derick_mitsui on 2009-05-27
Hi, i am a newbie in linux.
may i know how to setup kingsoft office using wine so that it can run properly in ubuntu?
cos i installed it and can run it, but the problem is i can't seems to open a file and save file. Is there any extra setting needed to run it properly?

I used this version of kingsoft office :
[http://download.famouswhy.com/kingsoft_office_2009](http://download.famouswhy.com/kingsoft_office_2009)

i heard that kingsoft office was cross platform applications but it's not working here. And i also heard that people can run MS office using wine and they did make a howto but no people ever wrote about how to run kingsoft office in linux before.

so can anybody here can help me solve my problem?? thanks in advance
Best regards

---

### Post by albinootje on 2009-05-27
> **derick_mitsui said:**
> 
i heard that kingsoft office was cross platform applications but it's not working here. 

Cross platform would be when they have a native Linux version available.

This [http://en.wikipedia.org/wiki/WPS_Office](http://en.wikipedia.org/wiki/WPS_Office) says :
> 
There are 2 version of WPS in Linux, WPS Office Storm(Clone from openoffice) and WPS 2005. Currently Kingsoft didn't support Linux since WPS 2007.


And this page is also not very clear about the Linux versions :
[http://ubuntuforums.org/showthread.php?t=702388](http://ubuntuforums.org/showthread.php?t=702388)

---

### Post by derick_mitsui on 2009-05-27
so particularly it can't run in ubuntu using wine??
i search the wiki and find this:
[http://en.wikipedia.org/wiki/LUK](http://en.wikipedia.org/wiki/LUK)

it shows the opened window of the WPS office but the problem is i also can open the application but the problem is it won't save. So are there any setting or dll in order to make the application run flawlessly (include saving), i mean like what they have done to microsoft office.

---

### Post by albinootje on 2009-05-27
> **derick_mitsui said:**
> so particularly it can't run in ubuntu using wine??
i search the wiki and find this:
[http://en.wikipedia.org/wiki/LUK](http://en.wikipedia.org/wiki/LUK)


Looks interesting.

I've just tried Kingsoft Office in PlayOnLinux with the default Wine, and the latest Wine 1.1.18, and in both cases it won't start properly.

And I've also searched the Wine database :
[http://appdb.winehq.org/objectManager.php?bIsQueue=false&bIsRejected=false&sClass=application&sTitle=Browse+Applications&iItemsPerPage=25&iPage=1&sOrderBy=appName&bAscending=true](http://appdb.winehq.org/objectManager.php?bIsQueue=false&bIsRejected=false&sClass=application&sTitle=Browse+Applications&iItemsPerPage=25&iPage=1&sOrderBy=appName&bAscending=true)
and there's no mention of Kingsoft Office.

---

### Post by deadlockedgamer on 2009-05-27
Try the open office built in if you need to save a windows doc it can do that too.

---

### Post by derick_mitsui on 2009-05-27
> **deadlockedgamer said:**
> Try the open office built in if you need to save a windows doc it can do that too.
The problem is if i use openoffice to open the document, the whole document messed up, i mean the margin ,setting, etc. I need to redo all the setting, that's wad freaked me out.
The kingsoft office is fully compatible with microsoft office, so i dont need to double work.

---

### Post by derick_mitsui on 2009-05-27
> **albinootje said:**
> 
And I've also searched the Wine database :
[http://appdb.winehq.org/objectManager.php?bIsQueue=false&bIsRejected=false&sClass=application&sTitle=Browse+Applications&iItemsPerPage=25&iPage=1&sOrderBy=appName&bAscending=true](http://appdb.winehq.org/objectManager.php?bIsQueue=false&bIsRejected=false&sClass=application&sTitle=Browse+Applications&iItemsPerPage=25&iPage=1&sOrderBy=appName&bAscending=true)
and there's no mention of Kingsoft Office.
So the wine don't have any interest to the kingsoft office huh?
there are a lot of compatibles applications there but sadly no compatiblity for kingsoft office. or maybe the current wine need a special setting or dll to make it able to save and open file.
So any linux guru here can have a test and experiment about it, thanks in advance.

---

### Post by deadlockedgamer on 2009-05-27
What open office version are you using? well any way i understand where you are coming from I had the problem with one doc at one point or another.

---

### Post by albinootje on 2009-05-27
> **derick_mitsui said:**
> So the wine don't have any interest to the kingsoft office huh?

You can probably make it work with LUK (which you gave a link to), but my impression is that people in China are either using MS-Windows, or using OpenOffice (or something else, like AbiWord maybe) in Linux.

And I think Wine is just like Linux a community based project. You can make an entry in the Wine app database, and describe which Wine version you used with Kingsoft Office, and what did not work, that'll be a start.

---

### Post by derick_mitsui on 2009-05-27
> **deadlockedgamer said:**
> What open office version are you using? well any way i understand where you are coming from I had the problem with one doc at one point or another.
I used the latest version of openoffice 3.10 but having problem like what i mentioned before, and finally i found the kingsoft office but sadly it wont work in ubuntu.

---

### Post by albinootje on 2009-05-27
> **derick_mitsui said:**
> I used the latest version of openoffice 3.10 but having problem like what i mentioned before, and finally i found the kingsoft office but sadly it wont work in ubuntu.

What do you need the office suite for exactly ?
Word processing, spreadsheets and perhaps more ?

There's Koffice,AbiWord, Ted, Gnumeric, and there's the commercial SoftMaker Office.

[http://www.koffice.org/](http://www.koffice.org/)
[http://en.wikipedia.org/wiki/AbiWord](http://en.wikipedia.org/wiki/AbiWord)
[http://www.nllgg.nl/Ted/](http://www.nllgg.nl/Ted/)
[http://projects.gnome.org/gnumeric/](http://projects.gnome.org/gnumeric/)

All of these are available from the Ubuntu repositories.

Here's a link to SoftMaker Office for Linux :
[http://www.softmaker.com/english/of_en.htm](http://www.softmaker.com/english/of_en.htm)

---

### Post by derick_mitsui on 2009-05-27
> **albinootje said:**
> What do you need the office suite for exactly ?
Word processing, spreadsheets and perhaps more ?
 
There's Koffice,AbiWord, Ted, Gnumeric, and there's the commercial SoftMaker Office.
 
[http://www.koffice.org/](http://www.koffice.org/)
[http://en.wikipedia.org/wiki/AbiWord](http://en.wikipedia.org/wiki/AbiWord)
[http://www.nllgg.nl/Ted/](http://www.nllgg.nl/Ted/)
[http://projects.gnome.org/gnumeric/](http://projects.gnome.org/gnumeric/)
 
All of these are available from the Ubuntu repositories.
 
Here's a link to SoftMaker Office for Linux :
[http://www.softmaker.com/english/of_en.htm](http://www.softmaker.com/english/of_en.htm)
 
I need it for word processing and spreadsheets mostly. I have a lot of ms office .doc & .xls files and when i opened it in OO.o the margin all messed up and i need to print that document monthly. For your information my office's PC use ms office as the office suite, then when i copy the file home to edit the work it juz cant sync. And if i set it accoding to OO.o setting, when i opened it in ms office it messed up too, so there's a lot of work so i m finding an alternative way n ppl intro me to the kingsoft office.
 
I've tried softmaker office but the result was the same. Koffice i never tried before, can Koffice run under gnome??

---

### Post by albinootje on 2009-05-27
> **derick_mitsui said:**
>  Koffice i never tried before, can Koffice run under gnome??

Yes.

You can of course also use MS-Office inside a MS-Windows guest VM in VirtualBox, or in Wine, or CrossOverLinux.

I just tested the LUK/Longene, and Kingsoft Office did start, I could not create a new document while it tried to connect, but then froze my machine completely.

---

### Post by deadlockedgamer on 2009-05-27
Well you could by crossover witch will support you run Microsoft office or you can use Google's online doc and spreadsheet app and just run it from work and home leaving you with an online doc that you can download any time

---

### Post by salvachn on 2009-05-28
The problem lies mostly in MS Office. The file format is mostly corrupt in older versions before 2007, so it may pose problems on other standards-compliant Office suites. I've experienced this a lot. Such documents work well in Abiword though. For spreadsheets, use Gnumeric.

---

### Post by derick_mitsui on 2009-05-28
> **salvachn said:**
> The problem lies mostly in MS Office. The file format is mostly corrupt in older versions before 2007, so it may pose problems on other standards-compliant Office suites. I've experienced this a lot. Such documents work well in Abiword though. For spreadsheets, use Gnumeric.
 
I will try using Abiword n Gnumeric also Koffice to see whether i get the best result. Btw i have already reported the bugs to wine, let's hope them can solved this bug so that the kingsoft office can be run in linux. 
 
I read about some article, it said the WPS Office Storm (kingsoft office china published name) can run on linux and it is said to be a wrapped version of windows application in wine but stop releasing now, n i can't seem to find a place to download it.

---

### Post by dmizer on 2009-05-28
> **derick_mitsui said:**
> The problem is if i use openoffice to open the document, the whole document messed up, i mean the margin ,setting, etc. I need to redo all the setting, that's wad freaked me out.
The kingsoft office is fully compatible with microsoft office, so i dont need to double work.
This is caused because the width of the open fonts are different from MSTT core fonts. Fortunately, it's easy to install them.

Install mstt fonts:
```
sudo apt-get install msttcorefonts
```
Then you need to make the msttcore fonts the default for Open Office. Formatting will be correct then.

---

### Post by PANGERAN on 2013-03-09
> **derick_mitsui said:**
> I read about some article, it said the WPS Office Storm (kingsoft office china published name) can run on linux and it is said to be a wrapped version of windows application in wine but stop releasing now, n i can't seem to find a place to download it.

Yes, right now WPS for Linux is available (although beta version for now)... you can read [my thread]("http://ubuntuforums.org/showthread.php?t=2121775").

---

