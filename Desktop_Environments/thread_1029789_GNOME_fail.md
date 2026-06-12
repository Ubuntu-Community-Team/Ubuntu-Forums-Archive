---
title: "GNOME fail"
date: 2009-01-03
forum: Desktop Environments
---

### Post by BenFischer on 2009-01-03
The other day I installed a few updates, and then firefox froze on me.  So I shutdown the computer and got sent to the recovery menu.  I selected fix xserver, and then boot normally.  Since then I have not been able to get my graphical display working.

I don't know if one of the updates messed up gnome, or if using fix x server was responsible. I've done a lot of searching and the most common solution was people reinstalling their OS... I would really perfer not to take that route.  How can I troubleshoot this problem to something more specific?

Here are a few of the things I've tried so far.

When I load the OS (Ubuntu 8.04.1 Kernel 2.6.24-22-generic) I have to change my console to see anything, and I encounter this.

###
Loading, please wait...
kinit: name_to_dev_t(/dev/disk/by-uuid/02a8589e-2006-4177-ab27-c643188ee718) = sda7(8,7)
kinit: trying to resume from /dev/disk/by-uuid/02a8589e-2006-4177-ab27-c643188ee718
kinit: No resume image, doing normal boot...
###
(This was apperently a common problem in fiesty, but not so much in heron.  I'm running heron though..)

Then I can log at any of the first six consoles, but not the graphical one, ctrl alt F7 does nothing. When I try running gdm at the command line I get this:

###
gdm: symbol lookup error: /usr/lib/libgtk-x11-2.0.so.0: undefined symbol: g_signal_accumulator_true_handled 
###

startx gives me my /var/log/xorg.0.log file as an error message.

---

### Post by Dave_Connor on 2009-01-03
sudo dpkg-reconfigure xorg-server

---

### Post by BenFischer on 2009-01-04
I tried it and got this 
###
Package 'xorg-server' is not intalled and no info is available. Use dpkg --info (-dpkg-deb --info) to examine archive files, and dpkg --contents (-dpkg-deb ---contents) to list their contents. /usr/sbin/dpkg-reconfigure: xorg-server is not installed.
### 
I tried sudo apt-get install xorg-server and to my dismay discovered my internet connection no longer worked either.  I don't know what happened but now suddenly I can't even ping google much less download packages.  

Edit: Fixed the connection.  Sudo apt-get install xorg-server gave me xorg-server is already the newest version. No new files were installed.

Thank you for the advice though, anybody else in the mean time?

Thanks,
Ben

---

### Post by Dave_Connor on 2009-01-04
You might have to reinstall. Make sure your stuff is backed up onto another computer with a direct connection or through an external drive and reinstall.

---

### Post by BenFischer on 2009-01-04
Sigh.. Ok so what files should I back up in order to maintain all my programs, files, and internet settings without reloading all the problems that exist now.  
I'll try this command 
tar cvpzf backup.tgz --exclude=/proc --exclude=/lost+found --exclude=/backup.tgz --exclude=/mnt --exclude=/sys --exclude=/dev --exclude=/sys
is there anything else I need to exclude though so that my old version of gnome and xserver won't mess things up?

---

