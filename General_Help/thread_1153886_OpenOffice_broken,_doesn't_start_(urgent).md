---
title: "OpenOffice broken, doesn't start (urgent)"
date: 2009-05-09
forum: General Help
---

### Post by m4lte on 2009-05-09
Hey guys, I'm facing some serious trouble as my OpenOffice is broken and I have some work to do.

I tried installing OpenOffice 3.1 ([http://ubuntuforums.org/showthread.php?t=1153050](http://ubuntuforums.org/showthread.php?t=1153050)) using the ppa from launchpad. Afterwards my OpenOffice didn't work any more.
So I went to the Synaptics Package Manager and completely removed all packages that turned up when I searched for 'openoffice'. (Acutally I left some packages which were not direclty related to OO, like spell checking stuff). Then I reinstalled OpenOffice (3.0!) from the Add/Remove software utility.

However, OpenOffice still doesn't work. When I try to start it, the splash screen sometimes appears briefly, but that's as far as I get.

**How can I get a working installation of OpenOffice again?**
Is there any log file that might hint at why OO is not starting?.


**EDIT:**
Now OO starts up again, however the interface doesn't look proper. The font in the menu is strange, and menus appear with a strange animation (appearing very large and then scaling down to the proper size).


**EDIT 2:**
Problem solved the rough way. I wanted to reinstall my system from scratch for a while. So I took the opportunity.

---

### Post by HuckleSmothered on 2009-05-09
O/S reinstall due to bad OpenOffice mojo, rough night ...

If it happens again, or to anyone else, one place to start is to remove the /home/<username>/.openoffice.org folder with all of your personal settings. I had a similar problem before which I traced back to my templates. Had to delete the templates before OOo would open again.

---

### Post by Psychoscorpic on 2009-05-10
Mine upgraded from Launchpad to 3.1 too - but has now disappeared from the Applications Menu!
Synaptic shows it as installed.
Not pleased.

---

### Post by HuckleSmothered on 2009-05-10
Hit *Alt-F2*, which will bring up the *Run Application* prompt. Type in *ooffice* here. This should bring up OpenOffice. 

You can use *Alacarte* to add a menu icon for it. This is found under *Preferences | Main Menu*

---

