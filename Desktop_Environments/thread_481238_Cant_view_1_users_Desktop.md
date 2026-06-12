---
title: "Cant view 1 users Desktop"
date: 2007-06-22
forum: Desktop Environments
---

### Post by Spidertrace on 2007-06-22
First of all just want to say thanks for everyone on this board.  Ubuntu is fairly new to me and have learned so much from all the great people on this site.  I apologize in advance for this lengthy post, but I wanted to be thorough this way we don't go back and forth trying things I already tried.

Anyway, down to business:

I'm running Ubuntu Desktop 7.04.  I've got everything I want configured and running great (ftp,apache,php,mysql etc..)

I have 4 users setup on the machine, one which is myself (of course).  Like an idiot, I tried changing the monitor resolution because my 19"LCD supports 1440X900 and have used that fine in Windows (which I happily have ditched Vista off my new machine for Ubuntu)
Well, know I cant login to the desktop of my account because after logging in, I get the black screen and my monitor says that it's out of range.

However, I can login with any of the other users just fine.  It's only after logging in with my username that the screen goes black.

Here's what I've tried:
I tried changing /etc/X11/xorg.conf file and removed the higher resolutions but that did not work.
I also tried changing the driver to "vesa" but that didnt work either.

I have a complete backup of the system from a couple of days ago when I tar'd the entire drive to a backup.tgz file on an external drive.    I even tried deleting the entire /etc/X11 directory and then I extracted the backup.tgz file on the Firewire drive and then copied the good /etc/X11 directory and it's contents over to main drive.

Although everything copied over fine, I still have the same problem.  All other users can login fine, but I get the black screen after entering my password.  This leads me to believe that there is another video configuration file somewhere besides /etx/X11 that is different for each user, does that sound correct?  After all I blew out the X11 directory and restored it from a known good backup and still have the same problem.  

I can ssh into my Linux box from my Mac with no problem if I need to make any changes.  Also I can do Ctrl>Alt >F1 at that black screen while on the Linux box to bring up a command prompt.  I just can't figure out where in the world the video settings are stored per user?

Any help would greatly be appreciated, or I'm just going to restore the entire box from my backup file.

Thanks everyone.

Joe

---

### Post by Happy_Man on 2007-06-22
That's odd... I had the same problem this morning, and I was able to restore everything by a simple "sudo dpkg-reconfigure xserver-xorg". Have you tried that?

---

### Post by Spidertrace on 2007-06-22
Thanks for the reply, but yeah I tried sudo dpkg-reconfigure xserver-xorg and used all the default settings.  But still have the same exact issue.  At this point, I'll probably just delete that 1 user profile and re-create it.  I've spent too much time troubleshooting, but would sure love to know what the heck happened.

Thanks
Joe

---

