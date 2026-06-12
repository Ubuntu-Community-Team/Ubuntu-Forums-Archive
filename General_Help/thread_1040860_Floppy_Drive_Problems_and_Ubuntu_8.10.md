---
title: "Floppy Drive Problems and Ubuntu 8.10"
date: 2009-01-15
forum: General Help
---

### Post by mperedithe on 2009-01-15
Good Evening Everyone,

Okay, here's my question for today.  I have got the new computer up and running.  I am running Ubuntu 8.10 with nothing else.  This is my first true and complete break from Windows (Yeah!!).  Everything is going fine, I configured separate x screens on my dual monitors.  However, I noticed that I have no access to the 1.44 floppy drive.  I know that this is old technology but I really need to get at the data.  The drive must be working because the bios checks it during each boot (as it is setup to do so).

Does Ubuntu 8.10 support Floppy drives?  How can I get it to see mine?  When the disk is inserted the drive does not respond with anything, no light, no sound.  Also the drive does not show up under the 'Places' menu.

Thanks in advance.
Marc

---

### Post by plucky on 2009-01-16
The driver is not loaded in 8.10.

To load the driver in a terminal ```
sudo modprobe floppy
```


And to load it for every re-boot ```
gksudo gedit /etc/modules
``` and add the word **floppy** on a newline.

If you are not confident editing system files,make a backup copy first ```
sudo cp /etc/modules /etc/modules.backup
```


Good Luck

---

### Post by mperedithe on 2009-02-07
Thank you Plucky, this seems to have done the trick.

---

