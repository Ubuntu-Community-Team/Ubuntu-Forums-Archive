---
title: "My panels are gone!"
date: 2008-01-15
forum: Desktop Environments
---

### Post by DAE_JA_VOO on 2008-01-15
My panels have just disappeared. I booted up and all my panels are gone!

What's going on? I can't even ALT-F2?!

---

### Post by Rowanmf on 2008-01-15
Ok , I have got the same problem , i did a fresh install of 7.10 two weeks ago , and have accepted all the updates that have been available since then .How ever i like to work with 4 desktops , and on my one and only panel i have a desktop switcher so i can click on any desktop at any time , the problem is that when i click on any of the 4 and go to that desktop my panel disappears and i cant move back to anywhere else , the only thing is to logout and log back in , i have tried alt f2 and then typing gnome-panel but that does nothing , i have tried playing with desktop affects but that does not have any affect , today it is slightly different , i cant click on any of the other desktops , they seem to be inactive (greyed out) even tho i moved thunderbird to desktop2 i cant touch it at all .
I have been reading the fault log reports for this started in an older version and all pionts to compiz , there was a comment to see what version you are running , mine says the correct version is installed but it does not report wheter it's running , well it does not look like it anyway , i will check with the manager just now , updates is running now so i have to wait .
if any one has any idea's ,, please 

Rowan

---

### Post by Kappity on 2008-01-27
Okay, this happened to me, I searched the forums, and I see I'm not the only one.  Here's some additional, specific, information in my case.

Xubuntu 7.10

My default session is XFCE, and I had the top and bottom panels set to auto-hide.  That is, move the cursor over them and they would appear.  Now, they won't come up.

I can right click on the desktop and get most of the stuff that I would get from the menu on the top panel.  However, the Panel manager doesn't  respond.

If I log out, and start a Gnome session, I do get the panels.  However, Gnome has other problems on this computer which I won't get into now.  It worked okay when I had Ubuntu, but when I changed to Xubuntu, and then installed Gnome as an afterthought, there were problems with it.  XFCE continued to work fine, though, until now.

I also don't get the workspaces selector that would normally be on the bottom panel.

This is not my main computer, and I could get by without it, but it's the one I brought with me tonight.  Any help in troubleshooting this appreciated.  I don't even know where to start, short of a complete re-installation, and that should hardly ever be needed.

[Addition]  I can open programs from the terminal (accessed via right click menu on the desktop) or with ALT F2.  However, who knows when something else wil go wrong. :(

---

### Post by Nycticorax on 2008-02-02
This isn't a solution to everyone's problems, but one way to get the panel back is to kill the current gnome-panel process (that makes a new one start automatically and the panel reappears). To kill it, issue the following command at a terminal:

```
killall gnome-panel
```

I posted the same thing on [this similar thread]("http://ubuntuforums.org/showthread.php?t=644107")

---

### Post by Kappity on 2008-02-02
> **Nycticorax said:**
> This isn't a solution to everyone's problems, but one way to get the panel back is to kill the current gnome-panel process (that makes a new one start automatically and the panel reappears). To kill it, issue the following command at a terminal:

```
killall gnome-panel
```

I posted the same thing on [this similar thread]("http://ubuntuforums.org/showthread.php?t=644107")

Thanks.  For me, the previous thread that you linked to solved the issue.  I typed ALT-F2 and "xfce4-panel", and the panels are back.

So for some reason, even after a reboot, the panel process was not starting.  I don't know if this had something to do with the updates that I download without thinking, or if it was something else.  I don't have time right now to check, but later I'll see if I have to manually restart the process each time I reboot, or if the computer will save this and do it automatically.

---

### Post by Bob Morane on 2008-02-10
Hello, slightly related issue here. I have a fresh, clean install of Gutsy, i'm using compiz-fusion with CCSM. I have enabled the desktop cube.
Sometimes, thought not every time, when i log in, my gnome panels are "invisible", i don't see them. However, they are running because if i change the virtual desktop using the cube, the panels will reappear on every desktop.

Weird!

If someone knows what's causing this, i'll be happy to learn. It's not really annoying since the fix is as simple as pressing 3 keys, but it's strange.

---

### Post by spectrevk on 2008-03-13
I'd rather recycle than create a new topic for something as simple as my problem, so here goes:

I only have two workspaces, and I would like to have four. I'm not sure why I only have two; this is a new ubuntu 7.10 install. I'm using the restricted driver for my ATI card (it's a Compaq Presario V5000, if that helps; bios is set to allocate 128MB to the video card). Is there a setting for this? I've looked all over preferences and I can't find anything.

---

### Post by doorknob60 on 2008-03-14
Right click the workspace switcher on the panel, choose preferences, and there you go :)

---

### Post by spectrevk on 2008-03-14
Thanks. Man, that really needs to go into the documentation. :)

I'm rapidly getting used to this OS...if I can just get my DVD playback working, internet at work (got some advice on that i'm gonna try tomorrow) and figure out some way to keep my trackpad acting right, I'll be set.

---

