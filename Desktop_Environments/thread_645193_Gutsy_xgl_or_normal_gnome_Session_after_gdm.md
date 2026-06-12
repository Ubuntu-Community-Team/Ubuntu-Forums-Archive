---
title: "Gutsy: xgl or normal gnome Session after gdm"
date: 2007-12-19
forum: Desktop Environments
---

### Post by dafu on 2007-12-19
hello,
i'm a notebookuser and i use ubuntu-gutsy gibbon. I have a ATI Mobility X700 graphiccard and so i need for compiz the xgl-server. At feisty it was possibil to choice in the gdm between normal gnome session and an session with xgl and if i started a xgl session then starts beryl  and at the normal session it did't start (at feisty i used beryl).  So i start in a normal gnome session on the way to save energie !!! Now my question : is it possibil to do this in gutsy ??  I want to choice between the an xgl-session and a normal session !! And if i start xgl then starts compiz !!

---

### Post by Prospero2006 on 2007-12-20
I'm going to bump this.
The solution I use right now is that I loaded xfce as a desktop option.
I use xfce when I need to disable the xgl. 
(For some reason I can't run GL apps on top of the xgl using my ati X300)
It's a school computer, so I don't have a choice, but I'll NEVER buy ATI as a personal card.

---

### Post by dafu on 2007-12-20
Ok xfce would be a solution but i don't want to change my desktop!! Have nobody an other idea to do that ?? I search many hours to found a way to do that at gnome but i didn't found nothing about my problem !

---

### Post by wayfarer_boy on 2008-01-09
I too am looking for a solution to this problem: how to create a session with XGL disabled.  What I don't want to have to do is create a new user account, as suggested here:

[[SOLVED] GUTSY - Create login session with XGL Disabled?]("http://ubuntuforums.org/showthread.php?t=616536")

I'm currently using the solution suggested in the thread (to disable XGL manually) by creating the disable file thus:

```
pico .config/xserver-xgl/disable
```

and saving the empty file.  I also use:

```
mv .config/xserver-xgl/disable .config/xserver-xgl/disable-backup
```

and log back in to revert back to XGL (in order to save me creating the file each time - it only saves a few keystrokes, I know, so it only makes it slightly faster than creating the file each time!)

Does anyone have a good solution to this rather frustrating problem?  I need a non-XGL session for things like Blender, StepMania, GoogleEarth etc.

---

