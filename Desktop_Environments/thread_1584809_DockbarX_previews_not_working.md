---
title: "DockbarX previews not working"
date: 2010-09-29
forum: Desktop Environments
---

### Post by discoross on 2010-09-29
0.39.7

Show previews is checked.
compiz settings: KDE Compatibility and Plasma thumbnails are checked

output when running in window:
> 
# dockbarx_factory.py run-in-window

** (dockbarx_factory.py:1860): WARNING **: Trying to register gtype 'WnckWindowState' as enum when in fact it is of type 'GFlags'

** (dockbarx_factory.py:1860): WARNING **: Trying to register gtype 'WnckWindowActions' as enum when in fact it is of type 'GFlags'

** (dockbarx_factory.py:1860): WARNING **: Trying to register gtype 'WnckWindowMoveResizeMask' as enum when in fact it is of type 'GFlags'
Dockbarx init
Dockbarx reload
Suggestions?


Edit: In all the threads about it, the selection Extras>Window Previews wasn't required. Selecting this under compiz-settings-manager worked for me.

---

### Post by M7S on 2010-09-29
Extras > Window Previews gives you compiz own previews, which are unclickable and will be on top of each other if you have multiple windows of a program opened.

The output you posted gives no clues of what the problem could be. Did you try to see a preview while running Dockbarx in window? 

If you use compiz 0.9, there's a weird bug that makes the previews show up behind the window list instead of above it. Otherwise, post a screenshot so that I can see in what way the preview is missing?

---

### Post by braikar on 2010-11-17
Hi,
Is there still no solution for this problem?

I have almost the same

dockbarx_factory.py run-in-window

** (dockbarx_factory.py:17741): WARNING **: Trying to register gtype 'WnckWindowState' as flags when in fact it is of type 'GEnum'

** (dockbarx_factory.py:17741): WARNING **: Trying to register gtype 'WnckWindowActions' as flags when in fact it is of type 'GEnum'

** (dockbarx_factory.py:17741): WARNING **: Trying to register gtype 'WnckWindowMoveResizeMask' as flags when in fact it is of type 'GEnum'
Dockbarx init
Dockbarx reload
Opened window matched with gio app on id: gnome-terminal
Opened window matched with gio app on id: ccsm
Opened window matched with gio app on id: firefox
Opened window matched with gio app on id: totem
Opened window matched with gio app on id: deluge
Opened window matched with gio app on executable: dbx_preference.py


the preview doesn't show (I have dockbarx 0.39.8, Compiz KDE compatibilty, plasma thumbnails and window previews actived) it doesn't work??
[[IMG]http://imageupload.org/dm-112900237695.png[/IMG]](http://imageupload.org/pm-112900237695.html)

---

### Post by braikar on 2011-01-12
Still no solution to this problem?
Btw. sorry M7S, seems like I ignored your reply :|, I have KDE compatibility set, preview window working on awn and as single window, but not grouped...

just installed version 0.42 and it still doesn't work, as you can see on the attached picture, it shows one preview, but not the 3 windows preview... actually it's showing previews like in the old dockbar 0.3x, when there were no grouped window previews...

[[IMG]http://img197.imageshack.us/img197/4618/screenshotej.th.png[/IMG]](http://img197.imageshack.us/i/screenshotej.png/)

---

### Post by braikar on 2011-01-12
could it be the startup command i use: "emerald --replace" to force window decorations, that is messing up the process?
I had a look there [http://ubuntuforums.org/showthread.php?t=1645175](http://ubuntuforums.org/showthread.php?t=1645175) that person has the same problem as me apparently and still no solution... well dockbarx adds to the gnome-panel on my system, but the previews still don't work..

I have
xprop -root | grep KDE, showing
_KDE_WINDOW_PREVIEW(_KDE_WINDOW_PREVIEW) = 0x0
so no problem there,

I'm on x64 Karmic and checked for lib64expat1, this one doesn't exist, however I have libexpat1 installed.
phython is working fine for many other scripts so I don't think there's an issue there

---

### Post by M7S on 2011-01-12
Try deselect and reselect kde compatibility plugin and plasma thumbnails. That worked for another person with the same problem. And deactivate the window preview plugin, it's not supposed to be used with ockbarx previews.

---

### Post by braikar on 2011-01-12
Hi,
I tried that already (KDE,plasma thumbs), it's not changing anything.
I disabled the 'window preview', that removes the bogus window previews, that's good.
But it seems the KDE window previews are hidden somehow, because the preview tabs eventhough they are empty register the correct size for the window.

---

### Post by M7S on 2011-01-12
Karthick had two problems, the preview one got solved.

[http://ubuntuforums.org/showpost.php?p=10264852&postcount=40](http://ubuntuforums.org/showpost.php?p=10264852&postcount=40)

---

### Post by braikar on 2011-01-13
I saw that in the thread :)
I tried that many times, turning KDE comp. on/off, not working
turning KDE comp. off, killing dockbarx, turning on KDE, starting dockbarx..
even with a reboot in between, it still doesn't change anything :(

---

### Post by 0N3 on 2011-01-13
0.42 is the latest version

sudo add-apt-repository ppa:dockbar-main/ppa

sudo apt-get update && sudo apt-get upgrade

---

### Post by braikar on 2011-01-14
I have dockbarx 0.42.1, got it from the web8upd ppa before it was in dockbar-main and the problem is still there. :(
Is there any difference between the 2 (web8upd/dockbar-main)?

---

### Post by braikar on 2011-01-14
I removed the web8upd version and set the ppa:dockbar-main, but the version iss only 0.30 there (how do you get the 0.42.1 from that repository? or is 0.30 the latest there for ubuntu10.10)... though that solved the problem somehow! the previews are working on version 0.30, so I'm happy :)
Thanks for the help

---

### Post by M7S on 2011-01-15
0.30 is the last update for Ubunut 9.10 in the official ppa. Is that what your using? That might be why it's not working for you while it works for others.

---

### Post by braikar on 2011-01-15
Oh yeah, right! sorry M7S I kept making the stupid mistake, karmic is 9.10 not 10.10... so yeah well that must be why only 0.30 works. :o
Then why do they make the dockbarx_0.42.1-1~webupd8~karmic_all.deb package available on webupd8 if it's not working? it should be mentioned somewhere :|

neobuller: well there are problems but at least I like that M7S the developer of it looks at all the problems of every user! high five for that :)

Btw. now that it works, I see that plasma thumbnails are not animated like compiz window previews, is there a reason why you chose to use plasma thumbnails and not the compiz version? perhaps to make dockbar also run on KDE?

I want to mark this thread as solved but the option is not available in the thread tools..

---

### Post by M7S on 2011-01-16
DockbarX 0.30 does not use kde plasma thumbnails. It kind of takes screenshots and shows them. This was slow and used quite a bit of memory so I switched to the plasma thumbnails in version 0.39. Kde plasma thumnails are animated and is used since normal compiz windows previews only shows up when howering a windows minimization area and can't be moved around or clicked.

I didn't know that plamsa thumbnails didn't work for karmic and I don't know if it's that way for everyone or if there are some other reason that it doesn't work for you. 

What I do know is that the problem should be is on Compiz side and not on DockbarX's side.

---

### Post by braikar on 2011-01-17
Hum well, I'll let you know if I ever find out the reason why dockbarx 0.39 and up doesn't work on my system :)

---

