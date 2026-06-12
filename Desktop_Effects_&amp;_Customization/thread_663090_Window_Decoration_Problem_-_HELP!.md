---
title: "Window Decoration Problem - HELP!"
date: 2008-01-09
forum: Desktop Effects &amp; Customization
---

### Post by rainai2k7 on 2008-01-09
Hi,

I have a problem regarding my window borders.  I can't change them no matter what I do.  This happened after I tried using the Sabayon LiveCD.

This is what I happened.  Last night, I logged on to Windows and ran VMWare Server.  I made a new virtual machine and configured it for a linux install.  I configured its CD drive to read from a Sabayon Linux image (.iso).  I was planning to run Sabayon as a "LiveCD" inside the virtual machine or install it in the virtual machine so that I could test it.  Anyway, when I tried to boot the virtual machine, the cd image loaded and I was presented with the Sabayon load menu.  When I tried to run Sabayon as a LiveCD, the loading got stuck on the part where it says "Initializing..." (or something like it) with that red progress bar.  I rebooted (the virtual machine) about 5-7 times and the same thing happened.  On my last attempt, I was able to get past it up to the log on screen.  But when I tried to log on, I got stuck again.  Anyway, I gave up.

This morning, I logged on to Ubuntu.  And look:
[IMG]http://i55.photobucket.com/albums/g132/RaiNai/bugged.png[/IMG]
My window borders have changed!!!  I use the default Ubuntu (Human) theme and window borders as it goes nicely with the general settings of my desktop and my wallpaper.  But, as you can see, I now have these red window borders that Sabayon uses!!!  And no matter what I try, I can't change the borders.  I have emerald installed.  I tried uninstalling it, but, it didn't change anything.  I tried going to System->Preferences->Apperance to open the "Appearance Preferences" dialog.  I tried changing the theme from here.  The theme of the controls (scrollbars, buttons) would change, but, the window borders would stay the same.  I tried customizing the theme and changed the window border.  Nothing would happen.

Can anybody try explaining to me why this happened and try helping me with this?  It is already annoying that I'm not a fan of these red window borders Sabayon uses.  It's even more annoying and frustrating when I can't change it!

Why did this happen?  In the first place, I only ran Sabayon in a virtual machine in Windows.  I was not even in Ubuntu!!  So why did I have my Ubuntu settings changed?!?! :confused:

Here are other things you may want to know about my setup.  I have two partitions on my internal hard disk.  I put Windows in the first partition and Ubuntu Gutsy in the second one.  For Ubuntu, I just use (or used) the default (Human) theme as I said.  You may also note that when I tried installing the emerald theme manager, I could not find any pre-installed themes.  I tried fetching the themes from its repositories (through the "Repositories" tab in the theme manager), but, my themes list would stay empty.  Another important thing you should note is that, in Windows, I can read from and write to my Ubuntu partition (ext3) through a Windows utility that allows me to "mount" ext2/3 partions on Windows.  I didn't do anything funky on my Ubuntu partition while I was in Windows last night, though.  I only copied some (music) files from my Ubuntu partition to my external/portable HD, which, is shared by both my Windows and Ubuntu.

Can anybody help me with this?  I'm still quite new to Ubuntu, and Linux in general.  So, please, if you care to help me, try using simple, layman's terms.

I'd really appreciate any help.

:confused:  This is frustrating!  :cry:

----------------------------------

Solved this issue myself...  I just reinstalled Compiz...  But, I'm still baffled about what happened... :confused:

---

