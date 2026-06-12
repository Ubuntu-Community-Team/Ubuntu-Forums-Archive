---
title: "Gnome Not Starting"
date: 2005-11-23
forum: Desktop Environments
---

### Post by pkraus on 2005-11-23
I have ubuntu breezy. I have installed the kubuntu-deskop metapkg and for today decieded to try it out so i set my session in gdm to boot kde and it worked. I then closed my session switched it back to gnome and logged in.

I get the splash screen then blank panels appear and flash for a few minutes then the vanish and its just sitting at an empty desktop. 

Tried restarting X, restarting the machine, nothing works. KDE works Gnome will not let me log in.

Paul Kraus:confused:

---

### Post by Sutekh on 2005-11-23
Sorry to be the harbinger of bad news...

I had the exact same problem after installing "kubuntu-desktop" just like you.
[http://ubuntuforums.org/showthread.php?t=88175]("http://ubuntuforums.org/showthread.php?t=88175")

awtomlinson seems to have the same problem after installing xine and vlc.
[http://ubuntuforums.org/showthread.php?t=86972]("http://ubuntuforums.org/showthread.php?t=86972")

Still haven't found a solution, but you can still log into KDE? which is a good start.  You may, as I did, be able to create a new user, who should be able to log into GNOME.  Logging as root should also work too.

---

### Post by pkraus on 2005-11-24
hmmm so its a user setting issue.
Is there a directory i can remove in my home directory that would wipe out all my gnome settings?

If another user works then the problem has to be some where in the users home directory.

Any gnome guys know which directories to remove to make it as if the user had never loaded up gnome?

Paul Kraus

---

### Post by Xian on 2005-11-24
[QUOTE=pkraus]
Is there a directory i can remove in my home directory that would wipe out all my gnome settings?
[/QUOTE]
There are multiple directories....
In your /home/username path look for:

.gconf, .gconfd, .gnome, .gnome2, .nautilus, .metacity and so forth.

---

