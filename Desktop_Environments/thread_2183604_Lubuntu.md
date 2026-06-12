---
title: "Lubuntu"
date: 2013-10-25
forum: Desktop Environments
---

### Post by mayagrafix on 2013-10-25
First I installed Ubuntu 12.04 with Unity-2D on a old laptop. Then I added Lubuntu desktop using the "apt-get install lubuntu-desktop" command line. It works great, using less than 100 megs of system RAM (512 total RAM).

So heres my question: Can Lubuntu become lighter (use less RAM) if I delete the Ubuntu desktop? (when I log in, I have my choice of desktops, either Unity2D or Lubuntu). 

I am loading unnecessary software upon start-up? I would like to have the OS as bare-bones as possible.

Disk space is not a problem, mostly unused HDD. The laptop sole use is to be a reader-viewer for PDF docs.

Thanks for any input :D

---

### Post by Dennis N on 2013-10-25
If possible, I would do a new install of Lubuntu from a Lubuntu ISO to avoid "unnecessary" packages for Lubuntu. You can't remove ubuntu-desktop components easily - if you remove the ubuntu-desktop package, you actually remove nothing much since it is a metapackage.

---

### Post by Bashing-om on 2013-10-25
mayagrafix; Hi !

Here is a thought, as you say:
> 
I am loading unnecessary software upon start-up? I would like to have the OS as bare-bones as possible.


How about considering installing as a "minimal install" and only adding what you want to that bare bones install ?

[INDENT][INDENT]to me simpler is better
[/INDENT][/INDENT]

---

### Post by mörgæs on 2013-10-25
Yes, the core install (based upon minimal) is a good beginning:
[https://help.ubuntu.com/community/Lubuntu/Documentation/MinimalInstall](https://help.ubuntu.com/community/Lubuntu/Documentation/MinimalInstall)

---

### Post by vasa1 on 2013-10-25
> **mörgæs said:**
> Yes, the core install (based upon minimal) is a good beginning:
[https://help.ubuntu.com/community/Lubuntu/Documentation/MinimalInstall](https://help.ubuntu.com/community/Lubuntu/Documentation/MinimalInstall)
The only problem with that is that doing a minimal install appears more difficult, at least to me, when compared to doing a clean install of Lubuntu (or whatever else). The installer is quite user-friendly and lets one **dual boot** which maybe a prime requirement for people hoping to try out "Linux" (without removing Windows) after XP support ends.

---

### Post by vasa1 on 2013-10-25
> **mayagrafix said:**
> First I installed Ubuntu 12.04 with Unity-2D on a old laptop. Then I added Lubuntu desktop using the "apt-get install lubuntu-desktop" command line. It works great, using less than 100 megs of system RAM (512 total RAM).

So heres my question: Can Lubuntu become lighter (use less RAM) if I delete the Ubuntu desktop? (when I log in, I have my choice of desktops, either Unity2D or Lubuntu). 

I am loading unnecessary software upon start-up? I would like to have the OS as bare-bones as possible.

Disk space is not a problem, mostly unused HDD. The laptop sole use is to be a reader-viewer for PDF docs.

Thanks for any input :D
I'm prejudiced against keep any other "desktop environment" around and not at all because of diskspace.

One will see more clutter in menus. Not all programs effectively use the "OnlyShowIn" and "NotShowIn" rules for .desktop files.

One will get updates pushed for all the DEs. Unity-related updates used to be very frequent. This maybe a concern for people with slow internet or bandwidth caps.

As for loading unnecessary software on start-up ... that can be properly tested if one sets up clean VMs for each DE and one VM for the hybrid. My ***suspicion*** is that things like **zeitgeist** and the famous **apt-xapian-index** will run in a Lubuntu session if the Unity desktop is present but (obviously) won't do so on a pure Lubuntu..

---

### Post by mayagrafix on 2013-10-26
Yes, I've come to the same conclusion, and will do a clean install of Lubuntu. Thanks for your advice.

---

