---
title: "Problem with the Unity launcher."
date: 2011-10-19
forum: Desktop Environments
---

### Post by celticsaxon on 2011-10-19
I'm using 11.10. When I log in to unity, right clicking the launcher icons will open menus but they do not work when they are clicked. Also, the launcher will dodge windows, but when a window is in full screen, the launcher wont reveal like it should when the mouse is moved to the left edge of the screen. The reveal mode for the launcher is set to "left" on ccsm. Has anybody else had this problem? And is there a way to fix it?

---

### Post by dave0109 on 2011-10-22
> **celticsaxon said:**
> the launcher will dodge windows, but when a window is in full screen, the launcher wont reveal like it should when the mouse is moved to the left edge of the screen. The reveal mode for the launcher is set to "left" on ccsm. Has anybody else had this problem?

Yes, I have the exact same problem on my Samsung NC10 netbook.  I've set the launcher to Dodge and Autohide to no avail.  It does not show itself when a window is maximised.  This is a major pain and is stopping me upgrading my parent's laptop as they don't use keyboard shortcuts.

All packages updated as of about 16:00 GMT.

---

### Post by remotusesse on 2011-10-25
Completely lost Unity &*#$, only get top menu with "File Edit View Go Bookmarks Help" no time, no power button, no nothing. Don't know what happen or how to get it back. I can login to my account in "Ubuntu 2D" and Unity is there? don't know what is happening, really sucks.

---

### Post by remotusesse on 2011-10-26
So my problem was I tried to use  Cube desktop through Compiz and it screwed things up for me. This worked for me, log in to Ubuntu 2D mode our to the terminal and do the following. 

$ sudo apt-get remove --purge compiz* 
$ rm -rf .compiz-1
$ rm -rf .gconf/apps/compiz* 
$ sudo apt-get install compiz compiz-core
$ sudo apt-get install unity 

Things are working for me again, hope this helps.

---

### Post by stinkeye on 2011-10-26
Usually this can be solved by re-enabling the unity plugin using ccsm.

---

### Post by dave0109 on 2011-11-05
OK, getting back on topic, the latest updates *appear* to have fixed the problem.  With windows maximised, the launcher seems to be showing up each time the mouse is moved over to the left.

---

### Post by Haven1 on 2011-11-06
> **dave0109 said:**
> Yes, I have the exact same problem on my Samsung NC10 netbook.  I've set the launcher to Dodge and Autohide to no avail.  It does not show itself when a window is maximised.  This is a major pain and is stopping me upgrading my parent's laptop as they don't use keyboard shortcuts.

All packages updated as of about 16:00 GMT.

If it is any help, I set mine to autohide with reveal mode on bottom left and it works perfect(edge revealtimeout @ 150). I chose bottom left and not top left due to chrome browsers' back button is on that top left corner.

---

