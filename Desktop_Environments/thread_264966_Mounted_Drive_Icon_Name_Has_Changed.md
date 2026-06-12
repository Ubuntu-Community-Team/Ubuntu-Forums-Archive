---
title: "Mounted Drive Icon Name Has Changed"
date: 2006-09-25
forum: Desktop Environments
---

### Post by A. J. Rimmer on 2006-09-25
I have my laptop set up for dual boot with Windows XP.  When I installed Ubuntu I also established an 8GB FAT32 partition so that I could easily exchange files between Windows and Ubuntu (since both OSs can read and write to FAT32).  Following the procedure in the Desktop Guide I have this partition set up to auto-mount to the folder /media/g (the partition is Drive G: in Windows).  This has worked fine for the past couple of weeks.  The drive icon appears on the desktop with the label "g" (without the quotes).

A couple of days ago I booted into Ubuntu and found that the name of the icon had changed to "ebian insta" (as in Debian installer, perhaps???).  It appears that a text string has become corrupted somewhere, but I can't find it.  I have fooled with the Configuration Editor, unmounted the partition, deleted the /media/g folder and created a new one named /media/winG, and done as much searching and fooling around as I can think to do, but the thing still appears as "ebian insta".

Everything functions OK, so this is a mere visual annoyance, but I'd like to learn how to fix it, if possible.  In the meantime I have used the Configuration Editor to turn off the Desktop icon, just so I don't have to look at it.  :rolleyes:  Of course, it still shows up as "ebian insta" in the Places menu.  :confused: 

Any suggestions, anyone???  Thanks in advance...

---

### Post by xmastree on 2006-09-25
What's the drive label in Windows? That's what drives usually show up as when mounted under media.

---

### Post by A. J. Rimmer on 2006-09-25
xmastree, thank you!  

That resolved the problem.  I had not assigned the partition a volume name in Windows, so apparently a stray text string was finding its way into the icon label.  I booted into Windows and gave it the name "WinLinShare", and that's what shows up in Ubuntu now.

I love these little problems ](*,) , at least when they have a happy ending. :p 

I did some more thinking about this as I worked around today, I had already decided to look at the Windows volume name, running Checkdisk, looking for a .hidden configuration file on the partition, etc.  Don't know if I would have thought of just assigning a name, though.  This little exercise also got me somewhat familiar with the Configuration Editor, and I learned some new things there.

Just the sort of mental exercise I was hoping to get with Ubuntu.

Thanks again! :KS

---

