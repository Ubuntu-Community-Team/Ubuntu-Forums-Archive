---
title: "Help: Beryl issues, found no helpful threads"
date: 2007-12-07
forum: Desktop Effects &amp; Customization
---

### Post by J_to_the_Putts on 2007-12-07
Alright so here is the deal

    On my machine I have Ubuntu Gutsy Gibbon 7.10 64-bit. 
    I installed beryl emerald-themes and everything was wokring fine except I had no window decorations (i.g. Title Bar and the minimize, restore down/up, and close buttons in the top right hand corner or the active window). 

 Now after doing some research I have found that it is a common problem and there are multiple fixes.  However all the threads I have gone to and posts I have discovered havent been much help to me. 

Ive tried emerald --replace and editing the xorg.conf file so that the colordepth was set to 24 and under "Device" adding Option "ADDARGXVisuals" "True" (or what ever the correct code is) and still nothing has helped. 

I tired reloading the xserver and the x-window manager and that made the problem worse. 

After doing that I ended up losing my whole installed desktop.  So i had to apt-get install ubuntu-desktop in the shell and got the desktop back. 

Now being pretty frustrated I was tired of this. 

So I decided to uninstall beryl emerald-themes and made sure that all the beryl and emerald packages where completly uninstalled. 

So I found a new thread and the users who replied to it seemed pretty happy with it and they seemed to be having no problems. 

However again installing beryl the way the user stated in the thread made matters worse. 

From time to time I would lose my desktop and be stuck at shell. 

I would have to su to root and "init 5" to get it back up after reboot. 

Beryl still is not functioning at all and the screen res keeps changing to 800x600 automatically. 

To make matters worse again now I cant even get Gnome working again as my default window and desktop manager.  What I think I am going to do is wipe out my system and do a fresh install of Ubuntu.
 
If anyone has any idea what could be wrong or knows of a good tutorial that has shown positive results a successful install please let me know.  Ive been trying to figure this out for a while now and have been unsuccessful at doing so

---

### Post by Xgen on 2007-12-08
I have no problems with Beryl in gnome Hardy Heron, in fact I run Beryl, Compiz, Kwin and Metacity window managers and can switch them on the fly...although I prefer Beryl.
I DID have problems with the original Beryl 0.2, as it wouldn't work with the emerald "git" version file that Compiz uses (loss of titlebars) so I had to downgrade to emerald 0.2...but then Compiz wouldn't work properly. But with the Beryl (svn?) version from [http://download.tuxfamily.org/3v1deb feisty eyecandy](http://download.tuxfamily.org/3v1deb feisty eyecandy) (added to the sources list), I can use the emerald "git" version and therefore the other window managers thru the Beryl tray icon. The only other changes I made (maybe unnecessary) - to the xorg file : 
Option  "AddARGBVisuals" "True"
Option  "AddARGBGLXVisuals" "True" 
Section  "Extensions"
    Option  "Composite" "Enable"
This is with an NVIDIA 5200 card.

---

