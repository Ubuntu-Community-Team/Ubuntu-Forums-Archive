---
title: "Problem getting Emerald Themer to apply"
date: 2010-03-18
forum: Desktop Environments
---

### Post by sahayes on 2010-03-18
Hi everyone,

I've searched for a solution to my problem, but haven't had any success yet. I want to use Emerald Theme Manager to apply a theme, and it won't apply. I've tried double clicking it. I've also tried typing emerald --replace in the terminal and got this:

> scott@scott-desktop:~$ emerald --replace
/home/scott/.themes/aero-clone/gtk-2.0/toolbar-custom.rc:21: Unable to locate image file in pixmap_path: "Toolbar/toolbar-black.png"
/home/scott/.themes/aero-clone/gtk-2.0/toolbar-custom.rc:24: Background image options specified without filename
/home/scott/.themes/aero-clone/gtk-2.0/gtkrc:187: Unable to locate image file in pixmap_path: "Arrows/arrow-up.png"
/home/scott/.themes/aero-clone/gtk-2.0/gtkrc:191: Overlay image options specified without filename Could anyone tell me how to get this to work? 

Thank you for your patience.

Scott

---

### Post by sahayes on 2010-03-18
Hi again,

I just wanted to post an update about what I've figured out so far.  I noticed that Emerald tells you what Ubuntu system theme you need to use with it.  The one I wanted to use called for Clearlooks, with Beryl blur turned on.  I couldn't figure out the second one, but I turned on Clearlooks, and now when I type "Emerald --replace", nothing happens in the terminal, and nothing changes on the desktop.  

I wouldn't normally post again so soon like this, because I don't want to seem "pushy," but I wanted to make sure that whoever helps me has all of the information.  Thanks again!

Scott

---

### Post by ssulaco on 2010-03-18
Try going into CompizConfig Settings Manager and entering "emerald --replace"
[http://ubuntuforums.org/showthread.php?t=860527](http://ubuntuforums.org/showthread.php?t=860527)

Its been awhile...but you may also have to log out/in

---

