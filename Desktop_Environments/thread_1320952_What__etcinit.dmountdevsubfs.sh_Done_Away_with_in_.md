---
title: "What?  /etc/init.d/mountdevsubfs.sh Done Away with in Ubuntu 9.xx?"
date: 2009-11-09
forum: Desktop Environments
---

### Post by oldefoxx on 2009-11-09
One of the things I've insisted on with Ubuntu and VirtualBox is support for USB devices.  I don't mean just external drives, but external printer, external scanner, and so on.

Since around Ubuntu 7.10, possibly earlier, one technique to activate USB support with Ubuntu has been to edit the /etc/init.d/mountdevsubfs.sh file and uncomment four lines, then make a suitable entry in the /etc/fstab.  It's worked, but lately the builds for Ubuntu had taken out the "Magic" lines in the above script file for enabling USB, and now with Ubuntu 9.10, I can't even find the file itself.  I could port the script file from an earlier Ubuntu install, and maybe that would work, but exactly what is going on here?  I've even read arguments on line that VirtualBox OSE should come with USB support built in, because (especially with notebooks and netbooks), external devices are going to be connected by USB.

Anybody that knows what they are talking about want to comment on this?
Is there a fairly easy way to get USB working in Ubuntu 9.10, or is it now incorporated in a way that avoids the need for a script file?  Or has it moved to some other startup script file?  Probably the middle choice, as my external backup drive is attached by USB, and being recognized right now, and I did nothing except to leave it attached when I upgraded 9.04 (new install) to 9.10 (immediate upgrade).

Oh, one issue I found about the elaborate slide show being shown during the 9.10 install is that it likely contributed to less disk space on the CD, meaning fewer applications included on The CD.  And it takes far more effort to add or remove applications with the new approach provided by the Ubuntu Software Center program under Applications.  Lots of practice typing in your user password for one thing, but if you keep moving ahead of the current application download, you can start one or two more, and your entered password has a small lasting effect, meaning you don't have to retype it each time for the next install if you can move ahead quickly enough.  I liked the old way much better.  You might even want to make sure a certain application is installed, walk through with the mouse, then find out that it is presently installed because you get the Remove instead of Install button at the end.  Not unattractive, but looks are not everything.  So that was just wasted time and effort when that happens.

---

### Post by mlo0352 on 2010-05-04
Bump.

I have been having the same problem.  I installed VirtualBox 3.1 using the update notification I got when I installed the non-OSE version of the program.  I installed the Device Package.  I have Windows 7 virtualized.  I looked around the menus and I have the usb things enabled, and I saw something about the filters, and tried adding individual devices, but no luck.  I have added myself to the vboxusers, and now I am just stuck.

Has anybody found a solution since this was originally asked?

Thanks in advance.

Oh yeah, and opening that file works, but I don't see any of the #Magic bit.

I am running Linux Mint. (sorry :P)

---

### Post by mlo0352 on 2010-05-04
Oh, and I pulled a "noob" mistake by not remembering to log out and log back in after changing the group status of my account, but even so, after restarting, I still have a grayed list of usb devices when i right click on the usb bit on the bottom while running the VM.

(The problem is still a problem that is to say...)

---

### Post by mlo0352 on 2010-05-04
Oh okay, so my first three posts here and I actually manage to fix my problem.  I rebooted completely and it worked.  I also added a bit of stuff to the fstab file in /etc, so I'm not sure which part of that worked (or if they both had to be done).

Anyways, now that I have this account, I will be asking more questions, and getting more and more used to having Linux as my main computers.:)

---

