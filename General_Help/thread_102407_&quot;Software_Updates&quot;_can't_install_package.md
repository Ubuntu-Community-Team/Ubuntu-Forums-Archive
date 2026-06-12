---
title: "&quot;Software Updates&quot; can't install packages. (tried the guideline, see the content)"
date: 2005-12-12
forum: General Help
---

### Post by Dislimit on 2005-12-12
Software Updates can't install. (tried the guideline, see the content)
I have updated my repository and I can search and install packages with Synaptic Package Manager now. The problem is that the "Software Updates" (activated by the little red icon in the top right of the GNOME window) Doesn't work well now. It can be opened, can reload updates, but when clicking "install" it just grey the window and then turns back and nothing else happens.


Here is what I've done:
1. updated the repository in the way introduced in the guide line.

2. created a "preferences" file:
    Package: *
Pin: release a=testing
Pin-Priority: 1

    Then:
gpg --keyserver wwwkeys.eu.pgp.net --recv-keys 1F41B907
gpg --armor --export 1F41B907 | sudo apt-key add -
sudo apt-get update

3. finding the problem introduced above, emptied sources.list, apt-get update.

4. change the content of sources.list into the following:
#deb cdrom:[Ubuntu 5.10 _Breezy Badger_ - Release i386 (20051012)]/ breezy main restricted

## Uncomment the following two lines to fetch updated software from the network
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy main restricted
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy main restricted

## Uncomment the following two lines to fetch major bug fix updates produced
## after the final release of the distribution.
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy-updates main restricted
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy universe
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy universe

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security main restricted

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security universe

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy multiverse

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy-backports main restricted universe multiverse

5. apt-get update, succeeded.

6. reboot the OS, but the above problem remains.

What shall I do?

---

### Post by RAOF on 2005-12-12
Well, you can manually install updates with "sudo apt-get upgrade", but I don't know why your update manager isn't working.

---

### Post by Dislimit on 2005-12-12
I have added a little infomation. Please check again.

---

### Post by carlosqueso on 2005-12-12
I have the same problem.  I think it's not our fault, but sadly, no updates have come through lately that I can use for the info on a bug report.  If you see the red thingy in the bar, could you run gksudo update-manager from the terminal and add it to [http://bugzilla.ubuntu.com/show_bug.cgi?id=20586](http://bugzilla.ubuntu.com/show_bug.cgi?id=20586) or post it here, and I'll take care of it.

---

### Post by ianpeters on 2006-01-11
[QUOTE=carlosqueso]I have the same problem.  I think it's not our fault, but sadly, no updates have come through lately that I can use for the info on a bug report.  If you see the red thingy in the bar, could you run gksudo update-manager from the terminal and add it to [http://bugzilla.ubuntu.com/show_bug.cgi?id=20586](http://bugzilla.ubuntu.com/show_bug.cgi?id=20586) or post it here, and I'll take care of it.[/QUOTE]

Hi, I just wanted to add myself to the list of people whose update-manager is broken in a similar fashion. Right now I have a pmount patch sitting in there and everytime I hit Install, it just flashes by and nothing happens.


EDIT: Something very strange happened. Just for kicks I right clicked the icon and told it to refresh the package list. I then entered the update-manager and suddenly there were more updates then just pmount. All downloaded and installed without a hitch. What is going on here? Isn't the update-manager supposed to check for new stuff all the time??

---

### Post by LoathRevolver on 2006-01-11
I've also been having this same problem recently. I just use apt-get via the terminal to get the updates I need. It's just as easy, and it works.

---

