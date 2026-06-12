---
title: "No free space, file size doesn't match"
date: 2011-02-17
forum: Desktop Environments
---

### Post by CovenStine on 2011-02-17
Hello,
In trying to solve a friend's lack of foresight, i have currently disabled my system.
I was using dd_rescue to make a copy of a drive with a corrupt and unfixable Partition Table.  I was a fool, and had a drive mounted to /media/Storage, but ran the backup to /media/storage.
Thus, dd_rescue completely filled my primary drive before informing me that there was a problem.
I don't really trust myself with command line work, so I foolishly sudo'ed nautilus and deleted the folder /media/storage.
Unfortunately, I didn't realize it, but the available space on the drive still read 0bytes.
I tried Terminal work to do a sudo apt-get clean command, but for some inane reason, the laptop screen won't support the display setting for the Terminal login, so I just had to hope that I was doing it right.
I wasn't, and decided to try working from a Live CD so I could see what I was doing.
the folder /root/.Trash/ doesn't exist on Ubuntu's install drive, and I can't figure out why the properties of the drive say "contents: 241310 files, 3.7 GB" but also "Total capacity: 52.8 GB.  Free space: 0 bytes"

Any suggestions on how I can get this to shake out?
Your help would be much appreciated, thanks
~C

---

### Post by gmargo on 2011-02-17
It must be in a trash directory somewhere.  Is there a /root/.local/share/Trash/?  The obvious thing is to use find to search the partition (using the LiveCD).  I'd start with:
```

find /path/to/mount/point -print | grep Trash

```

If you're having terminal size problems, you could run the SSH server on the LiveCD, and ssh into the box from another system.

---

### Post by CovenStine on 2011-02-17
Do files in a Trash folder not count towards the file/size counter in a folder properties dialogue?
*----answer: correct, anything in Trash-es will take away from "free space" on the drive, but won't contribute to file count/size shown in the typical dialogue.  They may show up in other ways, i don't know*

Is the search command case sensitive, if so, are all trash folders capitalized?
*----answer: yep, it is, all the **t**rash files/folders are apps/images/incidentals, whereas **T**rash folders are system folders*
Thanks,
~C

---

### Post by CovenStine on 2011-02-17
Thanks for the advise, worked like a charm.
Had to use sudo rm -r /Trash/directory/path to get rid of it, nautilus just kept making new trash files elsewhere.
~C

---

