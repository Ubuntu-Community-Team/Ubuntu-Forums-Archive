---
title: "MythTV + XBMC and NO window manager"
date: 2009-06-23
forum: General Help
---

### Post by Mattaus on 2009-06-23
Hi all,

Quick note: I am posting here because I feel this is not application specific and more of a general Ubuntu query.

Anyway...I am approaching the end of a build (finally) of a HTPC. The way it works is I have a customized MythTV Front End that launches on start up. Within that Front End , I have modified the menu structure, and among other things I have created a link that launches XBMC. The MythTV FE remains running in the background, and when XBMC is quit, The MythTV FE is ready to go again.

I am having a small problem - namely MythTV insisting on running behind the desktop task bars. This is another issue and not a question I am asking here - see this post if you know of a possible solution: 

[http://ubuntuforums.org/showthread.php?p=7506802#post7506802](http://ubuntuforums.org/showthread.php?p=7506802#post7506802)). 

However in an attempt to get my machine to boot faster a few weeks ago I discovered a method by which to launch XBMC without any window manager. I decided that this was how my final build would be as it is nice and clean and better suited to that "set top box" feel. I also realized that doing this would cure the task bar problem I had with MythTV. Yay for two-for-one solutions!

However as I am basically a Linux newbie and am unsure how to modify the following set of instructions in order to acheive the desired result. The following setup will launch XBMC and **only** XBMC upon startup of Ubuntu. I think I can change it to launch MythTV without any problems (simply exchange the "/usr/bin/xbmc" with "usr/bin/mythtvfront.real" or whatever it is) but how can I ensure that when I select XBMC from inside MythTV it will launch as well? I need MythTV to remain in the background. 

```
Login as the user who installed XBMC. 

Using your favourite editor, create a file in your home directory called .xinitrc 
that contains the following:
[B]#!/bin/bash
exec /usr/bin/xbmc --standalone[/B]

Make .xinitrc executable:
**chmod +x .xinitrc**

Edit your .bashrc and add the following as the last line:
**startx**

Install rcconf:
**sudo apt-get install rcconf**

Run rcconf and turn off gdm:
**sudo rcconf**

Install mingetty:
**sudo apt-get install mingetty**

Edit /etc/events.d/tty1:
**sudo vi /etc/event.d/tty1**

Change the line:
**exec /sbin/getty 38400 tty1**
to read:
**exec /sbin/mingetty --autologin uname tty1**
where uname is the user who installed XBMC.

Reboot to test.
```

Basically I need to tell Ubuntu to display the MythTV FE and XBMC and nothing else. (and XBMC obviously only launches when I tell it to do so with the menu in MtyhTV)

Is this possible? Have I been clear enough? I can elaborate if need be though I'm not totally sure what I can expand on lol.

Any assistance would be greatly apreciated.

Cheers.

- Matt.

---

### Post by rushikesh988 on 2009-06-23
why don"t you try to boot in recovery mode

---

### Post by Mattaus on 2009-06-23
> **rushikesh988 said:**
> why don"t you try to boot in recovery mode

I'm sorry but I'm not entirely sure how this would help me?

---

