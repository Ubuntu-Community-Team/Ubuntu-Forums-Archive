---
title: "Uninstalling Ubuntu problems..."
date: 2009-01-09
forum: General Help
---

### Post by StaticSpaz on 2009-01-09
Hey everyone, so I need to uninstall ubuntu from this laptop because it's going to be my dad's now, and i'm purchasing a new one. (He knows nothing of Ubuntu... and just wants Vista)
I have a dual boot setup going:
-Lastest version of Ubuntu
-Windows Vista
And so, I've been searching and searching around for a guide to uninstall ubuntu, but can't find one :) I know that I basically need to delete the partitions it sits in and change the mbr but is there a program that can do this all for me?
Also if I have to fix the mbr manually, when I repartition the hard drive with the Vista boot CD, and do it that way, It won't delete any files I have on the Vista partition right? I don't want to completely have to reinstall Vista.... :P

Sorry I know this is a lot of stuff but I'm trying to figure this out and I don't want to mess up this laptop before I hand it over haha.
Thanks!!!:D

---

### Post by blazemore on 2009-01-09
The easiest way to do this is with the Windows Vista disk. Do you have the disk?
If you do, put it in the laptop and boot from it.
Go to Install, and delete the Ubuntu partition (Or not, it doesn't matter)

Exit the installation (Don't accidently install Windows), and go to Repair, and run the recovery console. From there, issue these two commands:
```
bootrec /fixboot
```
```
bootrec /fixmbr
```

---

### Post by StaticSpaz on 2009-01-09
Hey thanks!! Ya I have the CD and I'll try this now. If I don't come back and respond, well it worked :D!
Again thanks!

---

### Post by upapilot on 2009-01-09
How can you do it without the CD?;)

---

