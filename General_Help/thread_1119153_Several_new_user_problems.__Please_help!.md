---
title: "Several new user problems.  Please help!"
date: 2009-04-07
forum: General Help
---

### Post by FLAGG0 on 2009-04-07
Take note, I'm not a computer genius, so please keep any answer simple ;) 

I tested Intrepid for a few days and liked it enough, so I ditched XP in favor of Linux on a backup computer that was more or less being used as a server.  I've been using Intrepid for about a week now, and it's driving me up a wall.  Some things that should be easy seem to elude me no matter how hard I try, so I've come for help.  

System info just in case:
Dell 8100
Intel(R) Pentium(R) 4 CPU 1700MHz
643MB
Ubuntu 8.10 (Intrepid)
NVidia GeForce 6200/AGP/SSE2
Sound Fusion CS46xx

Now to my problems....

1) Dual Monitors - Trying to install TV as mirrored monitor using S-Cable
 - System > Preferences > Screen Res doesn't even recognize another monitor
 - The Configure Display in the Notification Area does, but will not let me click 'Okay'
 - NVidia X Server Settings isn't working either.  It shows the TV as disabled, when configuring for Separate X screens it has me restart X, but it STILL doesn't work.

2) Shared Folders - Connecting External HDD on Ubuntu Machine to an XP Machine
I followed the various how-to guides everywhere and set up Somba per instructions.  The problem is the XP machine sees the Ubuntu computer, just nothing in it shared.  Is there something I need to load in XP for it to work?  I don't need to access anything on Ubuntu from XP.

3) Sound.  I have NONE!  The sound system hasn't changed since the conversion to Intrepid, but for some reason the ONLY sound I get is the annoying computer sound when I do something wrong.  No music, no movies, no sound at all.  Volume in Ubuntu is turned to max, as well as in VLC, Movie Player, Amorok, RhythmBox, the surround system, etc.  All cables and such are plugged in correctly. 
Some less important problems....

4) is there ANY way to change the Homepage in Ubuntu's version of Firefox?

5) Conky.  I tried to install it from these directions ([http://linuxowns.wordpress.com/2008/01/18/conky/](http://linuxowns.wordpress.com/2008/01/18/conky/)), everything went fine.  unfortunately when opening conky (alt+f2) I get.....nothing.  I've edited the conkyrc file several times, but nothing ever appears.

Someone please help me with ANY of these problems.  I've already re-installed ubuntu 3 times, I don't want to do it again. :(

---

### Post by maheshasolkar on 2009-04-07
> **FLAGG0 said:**
> 
4) is there ANY way to change the Homepage in Ubuntu's version of Firefox?


Go to the page you want to assign as your homepage. Drag the favicon (little icon on the left hand side of the address in address bar) over the Home button.

Or, go to Edit -> Preferences, in the Main tab, you can specify your home page.

> **FLAGG0 said:**
> 5) Conky.  I tried to install it from these directions ([http://linuxowns.wordpress.com/2008/01/18/conky/](http://linuxowns.wordpress.com/2008/01/18/conky/)), everything went fine.  unfortunately when opening conky (alt+f2) I get.....nothing.  I've edited the conkyrc file several times, but nothing ever appears.

Instead of using alt+f2, did you try running conky in terminal (Applications -> Accessories -> Terminal)? If not, can you try and see if any error message is issued. That may give some clue on why conky is dying.

---

### Post by mb_webguy on 2009-04-07
I can't help you with #1.  I don't have a lot of experience using multiple monitors except for connecting to a projector, and the times I have needed to do so, I didn't have any problems.

As for #2, if you had to follow a tutorial to configure file sharing... well, that's your problem.  Support for filesharing via Samba is built-in to Ubuntu since at least Hardy, if not earlier.  You need to go to Synaptic, search for samba, mark the package for complete removal, and uninstall it.  Now you can start over with a clean slate.

All you have to do is right-click on a folder you want to share, click "Sharing Options", check the box next to "Share this folder", and click Create Share.  The first time you do this, it will prompt you to install Samba.  Click Ok, and let it do its thing.  Now once again go to the folder, again click "Sharing Options" and the box next to "Share this folder", modify the options as you like, and click Create Share.

That's it.

If you install the system-config-samba package, it will give you a nice GUI configuration tool under System->Administration->Samba, where you can create and modify shares, and change your workgroup.

For #3, right click on the volume applet and Open Volume Control.  Look through each of the output devices to see if anything is muted or turned down.

For #4, do what maheshasolkar said.  You might also want to try uninstalling the ubufox package if you continue to have problems.

I also don't have anything helpful for #5, since I've only used Conky once for about 10 minutes before deciding it wasn't something I really wanted.

---

### Post by FLAGG0 on 2009-04-07
> **mb_webguy said:**
> You need to go to Synaptic, search for samba, mark the package for complete removal, and uninstall it.  Now you can start over with a clean slate.

All you have to do is right-click on a folder you want to share, click "Sharing Options", check the box next to "Share this folder", and click Create Share.  The first time you do this, it will prompt you to install Samba.  Click Ok, and let it do its thing.  Now once again go to the folder, again click "Sharing Options" and the box next to "Share this folder", modify the options as you like, and click Create Share.

That's it.

If you install the system-config-samba package, it will give you a nice GUI configuration tool under System->Administration->Samba, where you can create and modify shares, and change your workgroup.  

That's what I did the first time around.  Just re-installed it, everything works fine, but the XP machine still can't find any of the shared files.  Maybe it's a problem on that end instead of Ubuntu.

> **mb_webguy said:**
> For #3, right click on the volume applet and Open Volume Control.  Look through each of the output devices to see if anything is muted or turned down.  

That fixed it.  MAIN was not checked for some reason.  

As for #4.... that was a stupid moment for me... :lolflag:

Still can't get the monitors working if anyone has any ideas.  Did notice when clicking on the Configure Display Settings icon that there's another "monitor" picture, but it's not in the actual settings menu.  It's in the top left corner of my screen.  See here-> [Click]("http://i169.photobucket.com/albums/u238/scoobyd922/ConfigMonitor.jpg")


I also can't get Synergy to work, but I'm assuming it's for the same reasons as the file sharing. :-|

---

### Post by FLAGG0 on 2009-04-07
> **maheshasolkar said:**
> Instead of using alt+f2, did you try running conky in terminal (Applications -> Accessories -> Terminal)? If not, can you try and see if any error message is issued. That may give some clue on why conky is dying.

Actually, opening it in Terminal made it run right off. Go figure. #-o

---

### Post by FLAGG0 on 2009-04-08
Bump, in the hope someone can help with the monitor situation...

---

