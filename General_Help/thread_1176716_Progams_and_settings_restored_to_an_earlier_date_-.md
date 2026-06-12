---
title: "Progams and settings restored to an earlier date - problem"
date: 2009-06-02
forum: General Help
---

### Post by kavoura on 2009-06-02
I am running Ubuntu 8.04. What happened was as follows:

I lost internet access in Ubuntu 8.04, could not get access, although accessing internet from another PC worked fine.

I installed Ubuntu 9.04 in another partition, which worked fine including internet access, so I know it is not a hardware fault.

But when I booted back into Ubuntu 8.04 it was not working properly, I had only a low graphics login screen (with no error message) and the mouse and sound were not working. So I rebooted several times and still got the same thing, and then I tried editing the grub menu (using 9.04) to add an earlier kernel version, as some of the files for modules for the latest kernal in 8.04 were missing. It booted okay, and then I installed the latest kernel available for 8.04.

Then booted into 8.04 with latest kernel, but all the settings in programs like Firefox (incl. bookmarks) were all reset back to 21 Nov 2008, and all software installed since that date has vanished.

21 Nov 2008 is the date I last made backups of my home directory files. So I have had to reinstall software again and although I have lost my bookmarks (except for those saved in Delicious) I can carry on as best I can, but I would like, if possible, to recover missing files and settings from more recent times.

So why did my Ubuntu time-travel back to 21 Nov 2008? No data files were deleted, only software and settings. But it is like some kind of System Restore in Windows. Does this feature exist in some form in Ubuntu or is this some kind of freak system error? How did it manage to erase recent files and replace them with versions from over 6 months ago?:(

---

### Post by kavoura on 2009-06-02
I think I have realised what has happened in regards to the software and settings being out of date.

A few months ago I cloned the root partition, as a backup. Somehow, I have been running Ubuntu from the backup instead of the original, so the backup got updated. So when I installed Ubuntu 9.04, I chose the partition of the backup, thinking I do not need it any more, not realising that I was formatting and thus erasing my good installation of 8.04 and replacing it with 9.04, and when I booted into the old copy of 8.04 thinking it was the latest copy of my OS, I found instead an outdated version.

I feel so stupid now....

---

