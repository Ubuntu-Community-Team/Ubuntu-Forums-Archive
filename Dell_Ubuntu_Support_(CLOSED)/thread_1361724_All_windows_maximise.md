---
title: "All windows maximise"
date: 2009-12-22
forum: Dell Ubuntu Support (CLOSED)
---

### Post by teejayuu on 2009-12-22
Hi

Linux noob here and surviving with a Dell Mini 10v.  Just a quick question, every application I open is maximised and there are no Closed|Maximise|Minimise buttons - is this a default behaviour and can it be changed?  I am coming from a long Windows background (v3.0) and would like to see these button even when the window is maximised.  I know I can right-click the panel button (is that the correct terminiology for the taskbar), but the hand thinks quicker than the brain and automatically goes top right.

Apart from that I am generally pleased with the Dell and Ubuntu is a far superior distro than any other I have tried (Red Hat 3 (I think) and Mandrake 10).  Not sure I'm ready to give up on Windows yet as I need it for work, but would like to move more to a free environment.

Thanks
Tony

---

### Post by Matt__ on 2009-12-22
thats maximus in action for you...you could switch to the normal Ubuntu desktop if you dont want it to happen
(think its in preference menu...not got 10v in front of me atm)
I think I did see a post on editing a conf file to only max certain applications but I dont know how well it worked.

you could [check out this post too...](http://ubuntuforums.org/showthread.php?t=1252341&highlight=maximus)

---

### Post by jwaclawsky on 2009-12-22
That "maximus" program is just plain crap. I have had problems with it and I have found it's buggy and spoils what is a somewhat good working desktop. ...stay away from anything that use it. I am using a standard desktop 9.10 on my Dell mini 9 and it works just fine and, of course, no maximus.

---

### Post by mikewhatever on 2009-12-23
There is a config setting for maximus telling it not to maximize windows in gconf-editor, unser apps/maximus. Just run <gconf-editor>, navigate to apps/maximus and uncheck the box. Simple and elegant, no killing needed.

---

### Post by jwaclawsky on 2009-12-24
I tried the configure the settings for maximus on my mini 9 and it didn't work entirely. My problems became intermittent. I still think there is no reason for Maxumus except to inject undesirable behavior into what is a very good desktop. It truly is crap! 

My suggestion is just install ubuntu-9.10-desktop-i386.iso I updated my Mini 9 to this desktop version of Unbuntu three weeks ago and it has worked flawless (the only caveat is that you need to install the wireless driver when you are done) Just follow the instructions at:
[http://www.ubuntumini.com/2009/11/installing-ubuntu-910-karmic-koala.html](http://www.ubuntumini.com/2009/11/installing-ubuntu-910-karmic-koala.html)
It is not complicated at all if you are not doing any dual booting stuff. And you don't need to do any partitioning. Just do a simple install and it will work great. Make sure you do step 5 after the install to get your wireless working. 

BTW, my set up is a Mini 9 connected to a HP 25" monitor running at 1920x1080 with two cascaded USB hubs with CD burner, DVD burner, external hard drive. floppy drive, ZIP drive and HP wireless keyboard and mouse. Everything just worked when I plugged it in. Ubuntu 9.10 is damn impressive.

---

