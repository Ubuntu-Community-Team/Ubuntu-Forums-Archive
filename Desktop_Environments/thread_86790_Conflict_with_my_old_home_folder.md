---
title: "Conflict with my old /home folder"
date: 2005-11-06
forum: Desktop Environments
---

### Post by jyer on 2005-11-06
Hello,
I've just replaced my old Hoary by Badges, proceeding by a new installation of the latter.
I kept the same partition system that I used to have with Hoary, in order to keep my files in the /home folder (seems to make sens, doesn't it ;-). Namly:

hda5 /
hda2 /boot
hda3 swap
hda6 /home

Durung the installation, I formated hda 2, 3 and 5 so that Badges shall have plenty of place to install itself and doesn't get meddled up with my old files. I naturally kept hda6 as it was, to avoid anything happening to my files.
The installation went fine and Ubuntu 5.10 proudly booted. Only then did I realize I hade completly forgotten about all the hidden file (starting with a point . ) that had been automaticaly installed on my /home folder by Ubuntu Hoary. They seem to have come into conflict with my new ubuntu files, giving that now:

1.  As I open the session
I get a message indicating that .dmrc won't be loaded because user must be the owner and permissions must be 644. I therefore entered the following code:

sudo chmod 644 .dmrc

I then checked via Nautilus who confirmed that I (jyer) was now the happy owner of the file in 644 permission mode (rw-r-r). Nevertheless, Ubuntu still bugs me with is message each time I start.
Code:

root@razor:/home/jyer# ls -l .dmrc
-rw-r--r--  1 jyer jyer 26 2005-08-23 21:52 .dmrc

2. As the desktop loads
The following error message pops up:

Error activating XKB configuration.
It can happen under various circumstances:
- a bug in libxklavier library
- a bug in X server (xkbcomp, xmodmap utilities)
- X server with incompatible libxkbfile implementation

X server version data:
The X.Org Foundation
60802000

If you report this situation as a bug, please include:
- The result of xprop -root | grep XKB
- The result of gconftool-2 -R /desktop/gnome/peripherals/keyboard/kbd

I must say I'm a newbye on Linux system and this message is pretty close to Chineese for me...

3. My questions:
a. How could I have avoided such a conflict whilst installing my new version of linux  (please don't suggest updating)? 
b. I can't imaging one can simply delete this files while Gnome is running. Is there any command to do so via tpy2 (or other) and ask linux to delete all files starting with a dot . ?
c. Does anyone have an idea on how to resolve my problems?

Thanks a lot,

jr

---

### Post by paddyg on 2005-11-06
as for question a, i'll tell you what i did before upgrading--

i deleted all the hidden files and folders in my home dir after backing up all those hidden folders and files with important configurations (eg: bluefish, gftp, evolution mail, firefox bookmarks).

sorry i haven't got a clue for b & c

---

### Post by jyer on 2005-11-06
Thanks for your reply.
Here's a typical newbye question: can one delete all these files while running gnome without fucking everything up?
If not, is there a command line to do so quickly through tpy1 or 2?
Cheers,
jr

---

### Post by paddyg on 2005-11-06
if you've got a daredevil personality, just try the following

1. add a new user (system-->administration-->user and groups-->add user)
2. make sure new user has got the very same privileges you have
3. log out, then log in as root
4. as root, copy all your /home files and folders (NOT the hidden ones) and paste them to the new user's home folder
5. in terminal ```
chown -R newuser:newuser /home/newuser
```
6. log out, then log in as newuser
7. make sure everything is all right as newuser, then if so, delete your old self!

---

