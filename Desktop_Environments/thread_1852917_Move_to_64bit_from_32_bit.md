---
title: "Move to 64bit from 32 bit"
date: 2011-10-01
forum: Desktop Environments
---

### Post by PSBTornado on 2011-10-01
Hi

I am hoping to do a fresh install of 64 bit Natty. I currently run Natty 32 bit. My backups are taken care of by simple backup. Can I install 64 bit and then do a restore from my backups to keep all of my settings?

---

### Post by oldfred on 2011-10-01
Depends on what you have backed up. Some things should not be restored as the new versions are 64 bit. Do you have a separate /home or all of /home backed up? You can restore all of /home which is your data and user settings.

Programs cannot be restored as they are all 64bit, but you can export a list of applications and reinstall all the same as the 64bit versions.

from lovinglinux - use dpkg to list installed apps
[http://ubuntuforums.org/showpost.php?p=7157175&postcount=5](http://ubuntuforums.org/showpost.php?p=7157175&postcount=5)
[http://kevin.vanzonneveld.net/techblog/article/restore_packages_using_dselectupgrade/](http://kevin.vanzonneveld.net/techblog/article/restore_packages_using_dselectupgrade/)
From old install
dpkg --get-selections > ~/my-packages
From New install
sudo dpkg --set-selections < my-packages
sudo apt-get -y update
sudo apt-get dselect-upgrade

I only have a home system and little data changes daily. My backup plan is total reinstall, so I do not backup system but all the files and configurations I think I might need. If yo have made some system wide settings you may want to back up /etc, but I would not just copy it back as defaults may not be the same.

Oldfred's list of stuff to backup May 2011:
[http://ubuntuforums.org/showthread.php?t=1748541](http://ubuntuforums.org/showthread.php?t=1748541)

---

### Post by PSBTornado on 2011-10-01
The main things I would like to carry over are my email contacts and stuff like that. There isn't anything really that I can't just either make a copy of or just write down and re enter by hand. I would like to keep my game high scores and stuff too, but I can re enter those with gedit run as sudo.

From the sound of it a fresh start may be the go anyway. Most of my stuff I have stored is on a separate internal drive anyway.

Thanks oldfred.

---

### Post by jacksaff on 2011-10-01
If your /home is on a separate partition you don't need to erase it. Just install to a differrent partition for / and select the old home partition to be mounted as /home and make sure that it is not formatted during the install. If you create a new first user when you reinstall with the same name and password that user will automatically reuse your old home directory with all your settings and data.
Programs are on the root directory and so will get wiped. Synaptic can make a script for you so that you can reinstall exactly the same set of programs the next time round.
If your /home is on the same partition as / then you need to back it up somewhere. You should then be able to restore it into your new installation and use it as before.

---

### Post by 1clue on 2011-10-01
After lots of years of doing what you're describing, I recommend that you NOT try to restore your entire HOME directory.

Save your documents of course, anything OpenOffice or similar.  Pick a few things that really matter to you, and make sure they're backed up in more than one way.

For example, if you use evolution you should back up the "live" files, as well as exporting all your contacts separately.

While you're at it, save your web browser bookmarks too.

A good thing to do is go through your entire system, look at your settings and how you have things set up.  Every time I reinstall I have a few things I REALLY want consistent, but I always use the reinstall to change things up a bit.  Try out a new window manager, try out a different app for whatever purpose.


The thing is, 32-bit and 64-bit are usually in sync more or less, but not always.  Sometimes the 64-bit has a significantly different version number than the 32-bit, and the config files might not be compatible.  Apps generally can upgrade a config file but are lousy at downgrading them.

---

### Post by mibart on 2011-10-02
PSBTornado, would You mind if I ask: why do You want to install 64-bit version? Is there any single task that You can do better on 64-bit than on 32-bit? Just asking...

---

