---
title: "Unity desktop - icons missing, colours changed - ubuntu 12.04"
date: 2012-11-06
forum: Desktop Environments
---

### Post by ArlieS on 2012-11-06
Hi Folks,

I believe I'm running ubuntu 12.04, with the Unity window manager/desktop. 

My system has been working fine for months.

This afternoon, I clicked on the System Settings icon in the bar on the left of the screen. (It's not labelled, so I can never remember what Unity calls that bar.) I think I then selected "appearance". I did not change anything. Almost immediately after that a number of icons disappeared from the bar - I can still hover and get their names, or click on them, but there's no icon. Several screens have changed from purple to blue. That wouldn't bug me - it's nicer than unity's ubiquitous purple - but title bars are unreadable. 

I rebooted - no obvious change resulted.

I installed a large number of recent updates, using "sudo apt-get update" and "sudo apt-get upgrade", not the annoying GUI tool that sometimes appears on that left-side icon bar. No obvious change.

I rebooted again. Still no change. 

Missing icons include: "Home Folder", "Terminal", "system Settings", "Angband (X11)",  "Workspace switcher", and "trash" - plus any others where there's no hover-over text. 

Would anyone care to hazard a guess as to:
(1) what might have happened
(2) how one might fix it
(3) where to find useful documentation on unity, including where it keeps its icons, config files, etc., and which packages it uses? 
(4) whether this might have been caused by some kind of automatic update, and if so, how to identify and disable it? I really don't appreciate systems that suddenly stop working without me changing anything! If I wanted that, I could install windows. 

Thanks for any insight.

[Update - I've got a lot of complaints in $HOME/.xsession-errors, with things like:

** (gnome-control-center:2880): WARNING **: Could not find icon

This would be so much useful if the error message had included (a) what icon it was looking for (b) where it was looking.

At least it gives me a software component - with man page - to look at.

---

### Post by ArlieS on 2012-11-06
Problem solved - It appears I had accidentally changed theme from "ambiance (default)" to "High Contrast Inverse". (These are the labels used in the GUI tool.) "High contrast inverse" appears to be mapped to "Adwaita", when looking in directories for themes - but I have no /usr/share/themes/Adwaita

Bug report remains - 

1) Unity GUI components allow people to switch to non-existent themes
2) Unity GUI doesn't give the same theme names as are used elsewhere in the system, making finding appropriate files "exciting" 
3)  Given that there are 20 subdirectories of /usr/share/themes, and only 4 options in the GUI, it appears the GUI pays no attention to what is on the system it purports to configure
4) Given that AFAIK, I've done minimal changes to my X-related packages, starting with a normal desktop install, it seems that the pieces installed by default don't play nicely together. 
5) Still can't find what files to tweak to bypass the clearly defective GUI tools and configure my desktop in any reasonable way. 

This all started because I wanted to get rid of a unity misfeature apparently borrowed from Mac OS-X . When I have multiple windows of the same type (e.g. multiple firefox windows), there's no way to get a list of windows, with text titles, and select among them - all I can get is a set of too-small-to-read thumbnails, which rearrange each time I click one, so I can't even find the one I want by selecting them one after another. A friend told me that unity _was_ capable of handling this situation as well as tvtwm, windows, and just about every other window manager, so I was looking for what knob to adjust.

---

