---
title: "Save space? What can i delete? ..."
date: 2005-10-19
forum: Desktop Environments
---

### Post by NewWithoutClue on 2005-10-19
Name says it all.
What directories are save to clear?
in other words....
what in ubuntu/linux = "c:\windows\temp\*" ( windows 98 )
I think you will know what i mean....sorry if you dont

regards,
Paul.

---

### Post by whitewizardcoder on 2005-10-19
Usually, the temporary directory is "/tmp/".  It is (usually) safe to remove the contents of this directory.  Also, if you want to save more space, you can remove  cached packages from apt by running Synaptic Package Manager and clicking **Settings -> Preferences -> Files (tab) -> Delete Cached Package Files**.

Good Luck,
WhiteWizardCoder

---

### Post by NewWithoutClue on 2005-10-20
Thanks.


*the more you know..*

---

### Post by Blario on 2008-03-23
lol, I'm sure this list can be a lot longer.  I'm looking to save space in my /usr directory.  Disk Analyzer shows that /usr/lib is a full gigabyte, and so is /usr/share.  I got the operating system installed only 3 days ago....

./gnome is huge in /usr/share, which is basically because of its 'help' directory.  I notice that there are different languages there.  Can I safely delete these?  Any instances in which I'll need them?

 I also see that programs are basically installing in /usr/lib.  I thought software was supposed to install in /usr/ocal.... being the reason that I partition off'ed /usr/local....  Why are ubuntu packages such as openoffice & java-6-sun installing in there?

---

### Post by goodmanbrown on 2008-03-23
Sounds like you might be looking for localepurge.  I'd only use it if you really *need* space, though.  Not if you are just being finicky.  Here's the description from its deb package:

> Description: Automagically remove unnecessary locale data
 This is just a simple script to recover diskspace wasted for unneeded
 locale files and localized man pages. It will automagically be invoked
 upon completion of any apt installation run.
 .
 Please note, that this tool is a hack which is *not* integrated with
 Debian's package management system and therefore is not for the faint
 of heart. This program interferes with the Debian package management
 and does provoke strange, but usually harmless, behaviour of programs
 related with apt/dpkg like dpkg-repack, debsums, reportbug, etc.
 Responsibility for its usage and possible breakage of your system
 therefore lies in the sysadmin's (your) hands.
 .
 Please definitely do abstain from reporting any such bugs blaming
 localepurge if you break your system by using it. If you don't know
 what you are doing and can't handle any resulting breakage on your own
 then please simply don't use this package.


---

### Post by phyrewall on 2008-03-23
I definitely recommend fslint, which finds all file system "lint" like duplicate files (hash and crc compared). It also lists packages installed by how much space they take up, and will find temp files you can delete.

It also has the added benefit of finding bad file names, symlinks, and ids.

It's available in the Hardy repos via apt-get/aptitude/synaptic. Pretty sure it's in the Gutsy repos, but if not, here's a direct link to the latest version from the developers: [Here]("http://www.pixelbeat.org/fslint/fslint_2.24-1_all.deb")

(I just used it to sort a 200Gig drive full of a friend's downloaded stuff, got it down to 120Gig since it was full of dupes with different names/locations.)

---

