---
title: "Desktop went missing, appears solid black, no icons or files where they should be"
date: 2008-07-19
forum: Desktop Environments
---

### Post by diablo75 on 2008-07-19
I recently swapped out the motherboard on a PC for a friend.  He typically runs Windows XP on this dual-boot setup, and the last time I looked at the computer (before replacing the motherboard) everything looked good (in Ubuntu, that is).

After firing the system up in Ubuntu after the new board was installed, it seems his desktop (or at least the area of the screen where you expect to find the wallpaper and icons) is now pitch black.  There are files located in the ~/Desktop folder, but they are not appearing on the desktop itself, nor does the wallpaper.  Just solid black.

Everything else in the OS works just fine.

What might cause this to happen?

---

### Post by StickyCube on 2008-08-08
same problem here, though I've done no recent upgrading of hardware or software, except staying up-to-date with the automatic updates.  I've looked through all relevant sections I could find of gconf-editor, and they all appear to think the desktop and icons will display.

It would be excellent to get this back, but at least as a temporary workaround, could someone tell me how to properly unmount a removable drive if you don't have it's desktop icon?  I'm used to using the right-click menu.

---

### Post by StickyCube on 2008-08-08
*update*  I just discovered that starting nautilus from the command line brings back the missing icons and background.

Why nautilus wouldn't start normally confuses me, especially since I can browse files by navigating from the 'Places' menu (which used nautilus, I thought).
suggestions?

---

### Post by brujoand on 2008-08-08
> It would be excellent to get this back, but at least as a temporary workaround, could someone tell me how to properly unmount a removable drive if you don't have it's desktop icon? I'm used to using the right-click menu.


If the device is mounted at /media/disk you could do:

"sudo umount /media/disk"

And that will unmount the disk.

---

### Post by bthoward on 2008-08-27
I've got the same issue here after installing the latest kernel update 2.6.24.19-generic on a 64 bit mythbuntu box...  After the update the system booted into low video mode.  I downloaded the latest Nvidia driver compiled and installed it and rebooted and I was in this mode.  When in low video mode I still had a desktop and icons so it has something to do with these drivers it almost seems.

EDIT (seconds later): I just hit CTRL+ALT+BACKSPACE (didn't wanna reboot cause a show is recording right now) but that fixed me.  Not sure if I'm still going to have an issue when I reboot again but that probably won't be for weeks so I'm fine for now...  Perhaps its time to visit LaunchPad if this persists for me....

---

### Post by euchrid33 on 2008-11-04
I've been experiencing something similar - my wallpaper stays in place, but all the icons and files vanish.  I tried opening Nautilus (the trash can in my Avant dock, if it matters) and, like magic, the files and icons reappeared.

My concern is that I much prefer Thunar, and use it for all my file management.  Am I going to have to regularly open Nautilus to see my Desktop properly?  Is there some sort of conflict between the two?  I've used Thunar for ages without a problem.

---

### Post by jastonas on 2008-11-04
Have you tried
gconf-editor>apps>nautilus>preferences>Show desktop
?

---

### Post by euchrid33 on 2008-11-04
> **jastonas said:**
> Have you tried
gconf-editor>apps>nautilus>preferences>Show desktop
?

I took a look, and Show Desktop is already checked.

The problem with debugging this error is that I don't know what causes the icons to vanish, so it's really hard to test.

---

### Post by jastonas on 2008-11-04
Do you have any compiz plugins? Wallpapoz?
I just had a similar problem while playing yesterday with ubuntu..

---

### Post by euchrid33 on 2008-11-04
> **jastonas said:**
> Do you have any compiz plugins? Wallpapoz?

Nope.  The only compiz features that I'm using are transparent windows and shift switcher, nothing desktop or wallpaper related.  I did just notice that Show Desktop was unticked, I don't think that it matters but I've ticked it now.

---

### Post by jastonas on 2008-11-04
I didnt quite understand your problem, but if you are not using nautilus maybe the show desktop is useless, but if you use thunar, maybe you could try to find something similar to Show Desktop to see if its turned on.

---

### Post by euchrid33 on 2008-11-04
> **jastonas said:**
> I didnt quite understand your problem, but if you are not using nautilus maybe the show desktop is useless, but if you use thunar, maybe you could try to find something similar to Show Desktop to see if its turned on.

My problem is basically that when I boot my system, the desktop shows only the wallpaper.  No files, no icons, no context menu when I right click.  Once I open a Nautilus window, it all appears and it's fine.  This would be a pain if even if I used Nautilus, which I don't.

---

### Post by euchrid33 on 2008-11-04
Okay, I've got my problem fixed.  Not sure if its the same issue as the OP, but I'll post it here in case it helps someone in the future.

I discovered that if I ran the command 'nautilus' from the terminal when there weren't any icons on the desktop, it didn't open a nautilus window, but the icons did return.  So I went to Sessions (in the Preferences menu) and set that command to run on startup.

It's probably not the most elegant solution - it works around the problem, rather than identifying and solving it.  Nevertheless, my desktop works again.

---

### Post by rfm33428 on 2009-05-03
I Have the same problem, however maybe a different cause.  I tried running 'nautilus' in terminal & an error appeared basically saying that I have to go to the system administrator to enable user sharing.   
My isssue started after getting the distro-upgrade 9.04

My next step is learning how to enable user sharing in the system administrator.

Knock on wood, hopefully things will be fine for me after doing that.

---

### Post by dean2k on 2009-05-12
I had a very similar problem with Linux Mint 7 Gloria RC (built on Jaunty).  All my icons/trash/mounts went missing on the desktop and couldn't even right-click on the desktop.

Clicking and re-clicking show desktop didn't work.  CTRL-ALT-backspace didn't work.  etc. etc. etc.

My fix:  **apt-get install nautilus**

Not sure what happened to bung nautilus up, it was working fine one day then not the next.  Hope this helps someone else out :o

---

### Post by hezuo on 2009-11-10
I'm having the same problem. Unfortunately, the suggestions you have offered didn't work for my pc.
The desktop disappears everytime I change the display to 1280x1024, but it does appear when it's on 1024x768. Any help please?

---

### Post by gukid on 2010-01-05
hezuo:  I'm having the EXACT same problem, desktop is unavailable only if set to 1280x1024 resolution, all others work fine.  Though I'm running Linux Mint 8.

System:
P4 2.2 GHZ
512 MB pc3200 ram
Ati Radeon 8500
40GB WD IDE HD
Crappy MSI Motherboard

Any help would be awesome.

---

### Post by Musitektus on 2010-01-20
I'm having this exact same issue as those before me.  I am also running Linux Mint 8 at 1280x1024 just like hezuo and gukid. :(

Not much luck finding solutions at the Linux Mint forums so far, but I'm still looking.

---

### Post by Musitektus on 2010-01-20
well I've done some more searching and it seems that turning off ALL visual effects corrects the issue of the desktop not displaying at 1280x1024.  Hopefully that will only be a temporary fix so that I can turn Compiz back on someday.

---

