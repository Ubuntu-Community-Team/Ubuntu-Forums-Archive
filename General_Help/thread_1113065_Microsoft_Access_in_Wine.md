---
title: "Microsoft Access in Wine"
date: 2009-04-01
forum: General Help
---

### Post by gunksta on 2009-04-01
_**Introduction**_

This is my little Microsoft Access in Wine thread. The goal: Make it easier for Linux users to install and use Microsoft Access under Wine. Wine reviews will tell you it is not possible to use Access under Wine; they are wrong. With a few tricks, most things work with only a handful of exceptions (documented below). I have continued to update this guide as I learn more. If you have any problems or breakthroughs, I'd appreciate the info.

**History:** I originally started a thread that can be found [here]("http://ubuntuforums.org/showthread.php?t=1101477"), to learn more about using Access under Wine. I did not find the solution I was looking for, but I did receive a couple of interesting links that got me to thinking. I also read [this]("http://en.wikipedia.org/wiki/Microsoft_access") and [this]("http://en.wikipedia.org/wiki/Microsoft_Jet") to get more of an understanding regarding how MS Access works on Windows. When I found [winetricks]("http://wiki.winehq.org/winetricks"), things started to fall together for me.

______________________________________________________________________

_**Installation**_

These instructions have been tested on Jaunty x86 (I'm going to test it on my 64-bit machine soon). Because these instructions rely on winetricks, these  instructions may or may not work on older versions of Ubuntu.

Start with a fresh .wine directory. You can get this by moving or deleting .wine/. 
Run winecfg to set up a new .wine folder. 


[LIST=1]
[*]Download [winetricks]("http://wiki.winehq.org/winetricks") from the link.
[*]Start winetricks with: ```
sh ./winetricks
``` You will need to install:
[LIST]
[*]allfonts (This is really optional, but worth doing.)
[*]fakeie6 (Not necessary, but I hoped this would fix the help bug.)
[*]jet40 (this is absolutely necessary)
[*]mdac28
[*]msxml3
[*]msxml6
[*]richedit20
[*]richedit30
[*]vb6run
[*]vcrun
[/LIST]
[*]You may also consider installing colorprofile, comctl32, fm20, fontfix, fontsmooth-rgb and gdiplus.
[*]Install Office 2003. Office 2007 and newer use a different database engine that I don't know how to find/install. I do not know if Access 2007 works under Wine, but I doubt it.

[-- Office 2007 on Linux with Wine install guide]("http://www.wine-reviews.net/microsoft/office-2007-on-linux-with-wine-install-guide.html");
[URL="http://www.wine-reviews.net/microsoft/running-ms-office-2003-under-linux-with-wine-0952.html"]-- Running MS Office 2003 under Linux with Wine 0.9.52

[/URL]
[LIST]
[*]Mount the CD with the unhide option. Ubuntu automatically mounts the CD, so first you will need to unmount the CD (do NOT eject) and then re-mount it with ```
mount -t iso9660 -o unhide /dev/cdrom /media/cdrom0
```
[*]Do not install the native msi with winetricks if you are running Jaunty. This causes the Office Installation to abort, with errors to msi.
[*]Proceed with installation. I only installed Word, Excel and Access. The other programs are not interesting to me. I am most interested in Access.
[/LIST]
 
[*]Once you have successfully installed ofice, I suggest you create a backup of your .wine folder. This way, if you later install something that borks your configuration, you don't have to start from scratch to get an operational version of MS Office running. I use this to backup my .wine folder: ```
cp -R .wine .wine-<insert-current-date>
``` Having a backup of Access, which I need, makes me more willing to experiment with possible improvements or other applications that may or may not destroy my .wine configuration.
[/LIST]
______________________________________________________________________


_**Success! / Bugs! / Dunno!**_

The process I describe above worked for me (mostly). If it does not work for you, post your problems here! I do not guarantee anything and this may very well break with the next update (Karmic Koala) but it works for me today.

**What Works / What Don't:** There are some problems with Access. I suppose I would give it a Silver or Bronze star on WineHQ. (They prefer that users post reviews based on "pure" wine installations, which this is not so I won't sully their system with my review.) I appear to have basic functionality. The following functionality appears to work correctly:


[LIST]
[*]Create Tables
[*]Create / Run Queries
[*]Create / Run Macros
[*]Basic Forms appear to work
[/LIST]

However, there are some problems:


[LIST]
[*]Do NOT use any of the Wizards! They will freeze Access.
[*]The Help function tries to work, but displays empty windows.
[*]Office puts an icon into Ubuntu's Notification Area. Like other Wine apps, this tends to not look right and can cause some minor problems with other things in the notification area.
[*]"Create Query in Design View" has a minor problem. Normally when you start a query in design view, you are able to select the tables / queries you want to use as input to your query. In Wine, this dialog is ALWAYS empty, regardless of how many tables and queries are in the database. Workaround: Switch to SQL mode and complete the FROM your_table_here statement. If you then switch back to design mode, the table appears correctly.
[*]Decimal numbers look funny in table view and query view. For example, a number (double) that should be 360.234345 will be displayed as 3..60234345. In spite of the weird look. However, Access is using/calculating the number correctly. The problem appears to be related to the the display of the numbers. I can successfully export my query results to an excel spreadsheet, and the spreadsheet contains accurate decimal numbers that display correctly in Excel and OOo Calc. Depending on what you are doing, this bug may or may not be a big problem.
[*]Find is not usable. The text boxes for inputting the string you are looking for can not be selected. You can not use "find" to help you find the correct form.
[/LIST]

**What I have not done:**

I haven't tested everything and I honestly probably won't test everything. If you try something that I haven't had time to play with, please let me know.

[LIST]
[*]I have not tried to write any VBA script. I don't know if it works or not, but we have installed the VB stuff, so it may function correctly. As I mentioned earlier, macros do work, which may provide much of the functionality you need, but you may have to get a little creative.
[*]I have not developed any reports (yet). I will.
[*]I have not tried to use the Access web front-end. I will be surprised if this works.
[/LIST]

I hope someone finds this useful. Feel free to submit ideas, suggestions, etc. Report any problems you may have.

I will update this initial post form time to time as I learn more about Access and how to use it effectively in Wine.

---

### Post by gunksta on 2009-04-01
Just in case it's not clear why I posted this into the General Help forum, I **am** looking for help. I am looking for help in a couple of ways:

[LIST=1]
[*]I don't understand why the Wizards and Help don't work. I don't use the Wizards, but other people do. I'd like to figure out how to make them work, if possible.
[*]Like most Microsoft applications. Access is a bloated monster of an application. I don't use all of the functionality. My efforts will stay focused on the functionality that I need to use Access in my job. Others may have different needs. By posting this here, we can work together to solve each other's problems.
[*]I spent a lot of time reading and working on this. Most of the resources out there on the 'net say this isn't possible. With some effort, it is not only possible, it is usable. (At least, nearly as usable as it is on Windows.) I think there may be others out there who can benefit from this effort and this forum is looked at by many people.
[/LIST]

Another bit of useful information is this page on the [Community Documentation for wine]("https://help.ubuntu.com/community/Wine").

---

### Post by gunksta on 2009-04-01
I have to admit that this color of pink (Ha Ha, April Fools) must be the ugliest color ever presented on a computer screen.

---

### Post by Shippou on 2009-04-01
> **gunksta said:**
> I have to admit that this color of pink (Ha Ha, April Fools) must be the ugliest color ever presented on a computer screen.

No; all white is. As in SHINING, SHIMMERING WHITE.

I do hate white backgrounds. I love black bgs. 

Sorry; this is quite off-topic.

---

### Post by marl30 on 2010-12-10
This tutorial worked for me. Was able to install and run Access 2003 successfully. It's running quite well and stable so far. I'm using Wine 1.3.8.

---

### Post by fatharraxman on 2010-12-10
cheers :D

---

### Post by marl30 on 2010-12-10
One thing to take note of though. If you have a none service pack version, do not upgrade it after installing the Winetricks additions. It will cause Access to stop working. I did that and ended up having to formate Wine. It's a good thing I have Office 2007 on PlayonLinux, and haven't reinstalled my games since reinstalling Ubuntu a few days ago, so I only lost basic stuff that can be easily reinstalled. I installed Office 2003 and only added the newer office compatibility installation this time around, and Access works like a charm. :)

---

