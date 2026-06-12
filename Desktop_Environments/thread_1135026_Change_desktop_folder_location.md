---
title: "Change desktop folder location?"
date: 2009-04-24
forum: Desktop Environments
---

### Post by petermoffat on 2009-04-24
I'm almost sure I've done this before, but after installing Jaunty last night, I an't seem to make it stick..

I'm trying to change the location of the desktop folder from $HOME/Desktop to a folder on another drive

Ive created a symbolic link to the folder I want to use, and edited .config/user-dirs.dirs (I think) to use this location, however, when I reboot, the desktop contains the contents of my $home folder, as the edit is no longer there, i.e. what I changed to $HOME/Desktop, is now $HOME/ . I deleted the Desktop directory when I started which is when the user-dirs.dirs started acting up I think?

Also, the new folder is on another drive (I like to use my desktop as a temp storage place for things I currently use, and use the same one between various OS's windows XP and 7 as well as ubuntu, so that I can get on with things more efficiently no matter what os I'm using.)

The disk is an NTFS partition is specified in fstab, though I suspect this is not correct, as my symlink does funny things on reboot until i've actually opened the drive in nautilus, so i suspect that it may not be mounting automatically on reboot?

Please help!

Also, well done on getting just about everything to work on my Samsung nc10, apart from iffy brightness and the mouse movement feeling a bit wrong, It's so good to have ubuntu on my primary pc again!

---

### Post by NESFreak on 2009-04-24
looks like it is indeed not mounted on startup.

try fiddling with this [https://help.ubuntu.com/community/Fstab](https://help.ubuntu.com/community/Fstab) Its where the drives that are mounted on startup are listed.

Maybe it would also be helpfull if you listed your fstab here.

---

### Post by petermoffat on 2009-04-24
Don't have the PC with me now, but will paste my fstab when I do, had a look at the fstab spport page earlier and will have a look when I have time as well, copied the line from a site this morning, so it may not be right.

---

### Post by petermoffat on 2009-04-25
Did a fresh install and set a mount point for the drive during partitioning, then changeed the location as I was doing earlier, .config/user-dirs.dirs and all works now

---

