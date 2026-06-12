---
title: "missing ia32-libs in updates"
date: 2009-04-18
forum: General Help
---

### Post by Maximusmaximus on 2009-04-18
hello all, 

sorry if this is a complete n00b question, but every time i try to update something i all ways no matter what i am updating get the error message

E: Couldn't find package ia32-libs

i currently run 8.04. is this a problem? because it seems to interrupt the terminal in whatever it is doing.

---

### Post by Yashiro on 2009-04-18
Sounds like you need to enable the universe and/or the security repositories.

System Menu > Administration > Software Sources.
Check that all the repositories are enabled.

Then run *sudo apt-get update* from a terminal.
Followed by *sudo apt-get install ia32-libs*

Or just download and install the correct version from here: 
[http://packages.ubuntu.com/](http://packages.ubuntu.com/)

---

### Post by Maximusmaximus on 2009-04-18
and i did check the that all of the repositories were enabled but and it updated itself, and then i did the terminal commands

when i ran sudo apt-get update i got these error messages:

W: Failed to fetch cdrom:[Ubuntu 8.04 _Hardy Heron_ - Release i386 (20080423)]/dists/hardy/main/binary-i386/Packages.gz  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs

W: Failed to fetch cdrom:[Ubuntu 8.04 _Hardy Heron_ - Release i386 (20080423)]/dists/hardy/restricted/binary-i386/Packages.gz  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs

E: Some index files failed to download, they have been ignored, or old ones used instead.


and when i ran sudo apt-get install ia32-libs i got this error message:


W: Duplicate sources.list entry [http://packages.medibuntu.org](http://packages.medibuntu.org) hardy/free Packages (/var/lib/apt/lists/packages.medibuntu.org_dists_hardy_free_binary-i386_Packages)
W: Duplicate sources.list entry [http://packages.medibuntu.org](http://packages.medibuntu.org) hardy/non-free Packages (/var/lib/apt/lists/packages.medibuntu.org_dists_hardy_non-free_binary-i386_Packages)
W: You may want to run apt-get update to correct these problems
E: Couldn't find package ia32-libs

---

### Post by Yashiro on 2009-04-18
Ok. Open the Software Sources Applet again.
On the first tab untick or disable the reference to the cd source at the bottom of the window if it exists.
Tick every box on this tab except the 'source code' box.
In the 'download from' drop down selector, change the download server to another server.

Click the next tab. Third party sources.
Disable everything in this window.

Click the next tab. Updates.
Make sure only the top two boxes of the upper four are selected.
Exit this applet.

Open a terminal and do sudo apt-get update.
Please post the contents of your /etc/apt/sources.list in your next post.

Now, you are actually running an i386 build. Which suggests you shouldn't even need ia32-libs. Which are usually for 64bit systems. 
Have you tried to force install a 64bit package or something like that? 
Or perhaps an ati/amd gfx driver?

---

### Post by Maximusmaximus on 2009-04-19
done what you asked and everything worked this time with no error messages. i am not sure if this is exactally what you want for the sources.list;

# deb cdrom:[Ubuntu 8.04 _Hardy Heron_ - Release i386 (20080423)]/ hardy main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hardy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hardy-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hardy universe
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hardy-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hardy multiverse
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hardy-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) hardy-backports main restricted universe multiverse
# deb-src [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) hardy-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hardy-security main restricted
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hardy-security universe
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hardy-security multiverse
# deb [http://download.tuxfamily.org/3v1deb](http://download.tuxfamily.org/3v1deb) feisty eyecandy
# deb-src [http://download.tuxfamily.org/3v1deb](http://download.tuxfamily.org/3v1deb) feisty eyecandy
# deb [http://ppa.launchpad.net/reacocard-awn/ubuntu](http://ppa.launchpad.net/reacocard-awn/ubuntu) hardy main
# deb-src [http://ppa.launchpad.net/reacocard-awn/ubuntu](http://ppa.launchpad.net/reacocard-awn/ubuntu) hardy main
# deb [http://packages.medibuntu.org/](http://packages.medibuntu.org/) hardy free non-free
# deb-src [http://packages.medibuntu.org/](http://packages.medibuntu.org/) hardy free non-free

---

### Post by Yashiro on 2009-04-19
So you're all fixed now, yes?

---

### Post by Maximusmaximus on 2009-04-19
seems like it thank you for all the help. ill post again if thre are any more issues

Max

---

### Post by Yashiro on 2009-04-19
No problem. :)

---

