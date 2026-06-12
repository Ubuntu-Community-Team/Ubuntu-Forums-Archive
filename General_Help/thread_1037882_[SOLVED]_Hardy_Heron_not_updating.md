---
title: "[SOLVED] Hardy Heron not updating"
date: 2009-01-12
forum: General Help
---

### Post by Robster2 on 2009-01-12
I updated from Gutsy Gibbon to Hardy Heron fairly soon after it came out.

It has been running very well until now.  When I run the update manager it downloads 75 files then I get the following error message.  When I close the error window none of the updates are installed'


"Failed to fetch cdrom:[Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016)]/dists/gutsy/main/binary-i386/Packages.gz  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
Failed to fetch cdrom:[Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016)]/dists/gutsy/restricted/binary-i386/Packages.gz  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
Some index files failed to download, they have been ignored, or old ones used instead."

Ubuntu Hardy Heron is great. Please help me with my problem.

---

### Post by Elfy on 2009-01-12
Open software sources in the system admin menu and disable the cdrom's, while ther check that the repos on the front page are enabled and that proposed and backports on the update page are disabled - unless you know you wnat them enabled, close and it will prompt to reload let it.

Then the update manager should work for you.

---

### Post by DeMus on 2009-01-12
> **Robster2 said:**
> I updated from Gutsy Gibbon to Hardy Heron fairly soon after it came out.

It has been running very well until now.  When I run the update manager it downloads 75 files then I get the following error message.  When I close the error window none of the updates are installed'


"Failed to fetch cdrom:[Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016)]/dists/gutsy/main/binary-i386/Packages.gz  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
Failed to fetch cdrom:[Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016)]/dists/gutsy/restricted/binary-i386/Packages.gz  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
Some index files failed to download, they have been ignored, or old ones used instead."

Ubuntu Hardy Heron is great. Please help me with my problem.


Is it possible you need to put the 7.10 disc in your disc drive? It looks to me you still enabled this repository. To avoid getting this question is:
1. Put the 7.10 disc in the drive
2. disable the 7.10 cd-rom as repository. Do this:

Menu System | Administration | Software sources.
Type your password
On tab Third party Software disable: CDRom 7.10

DeMus

---

### Post by Robster2 on 2009-01-12
Thanks for the replies now it downloads 66 files.  I have disabled the cdrom update on the software sources.

I do not get an error message but I do not get prompted to install the updates like I used to. 

The update manager says it is up-to-date but each time I press check it downloads the same 66 files.

Is my problem fixed?

---

### Post by DeMus on 2009-01-12
> **Robster2 said:**
> Thanks for the replies now it downloads 66 files.  I have disabled the cdrom update on the software sources.

I do not get an error message but I do not get prompted to install the updates like I used to. 

The update manager says it is up-to-date but each time I press check it downloads the same 66 files.

Is my problem fixed?

With: "but I do not get prompted to install the updates like I used to" you mean like in 7.10?
I don't know that version, I started with 8.04.
On top of the window does it say your system is up to date?
When I click: Check now it also downloads files but after checking it says that my system is up to date.
Please check this and if it is like I suspect your system is up to date and no updates need to be installed.

Demus

---

### Post by Elfy on 2009-01-12
Do

```
sudo apt-get update &&sudo apt-get upgrade
```

---

### Post by Robster2 on 2009-01-12
Thanks to all replies.

Looks like my system is up to date.

---

