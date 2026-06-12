---
title: "&quot;Open with&quot;-Menu filled with duplicates"
date: 2010-01-22
forum: Desktop Environments
---

### Post by Klaue on 2010-01-22
Hi there
I searched the forum, but the only similar thread I was able to find was no help..
When I right click on a random file and choose "open with"->"other application", my apps list is overloaded with duplicates. Some items in particular are there numerous times (for example, Hex Editor: 7 times).
Is there a way to clean this up? (the remove-button stays greyed out)

Ubuntu 9.10 - But I had that problem since 7.10 or so.

---

### Post by user1397 on 2010-01-23
> **Klaue said:**
> Hi there
I searched the forum, but the only similar thread I was able to find was no help..
When I right click on a random file and choose "open with"->"other application", my apps list is overloaded with duplicates. Some items in particular are there numerous times (for example, Hex Editor: 7 times).
Is there a way to clean this up? (the remove-button stays greyed out)

Ubuntu 9.10 - But I had that problem since 7.10 or so.
did this happen only after installing kubuntu-desktop side-by-side with your original ubuntu installation?

---

### Post by Klaue on 2010-01-23
No, I never installed kubuntu-desktop
The only KDE packets I have are those needed to run KDE-Programs like K3b

EDIT: The problem is not only with KDE programs - the multiple listed hex editor is, for example, ghex, a gnome utility

---

### Post by Klaue on 2010-01-26
bump?

---

### Post by orangemoose on 2010-01-31
I went to this directory and removed all the entries.

~/.local/share/applications/

That took care of MOST of the duplicates.

Still have not figured out how to get rid of the standard icon duplicate.

---

### Post by mister_playboy on 2010-02-17
> **orangemoose said:**
> I went to this directory and removed all the entries.

~/.local/share/applications/

That took care of MOST of the duplicates.

Still have not figured out how to get rid of the standard icon duplicate.

Thanks for this fix!  I've been screwing around with Wine and I was sick of seeing the 50 duplicate entries for rundll32, WinRAR, etc. :roll:

I really don't understand why the Remove button is grayed out... :?

---

### Post by lunatico on 2010-04-28
Thanks! Removing stuff from ~/.local/share/applications/ worked form me too. Annoying thing.

I also wonder why that remove button does not work. I tried opening nautilus as root but remove is still grayed out.

It must be some silly thing...

---

### Post by jasontan6 on 2010-05-11
I also tried removing things in ~/.local/share/applications, it got rid of most of the useless entries created when installing apps using Wine, but not some of the packages which i think were upgraded. At the moment i have 2 Brasero, 2 F-Spot and 2 Remote Desktop Viewer.

---

### Post by 45acp on 2010-05-30
I have the same, 2 Brasero, 2 F-Spot and 2 Remote Desktop Viewers, Can't figure out how to get rid of the duplicates.

---

### Post by bruwstout on 2010-07-27
Same here with the 2 Brasero, 2 F-Spot and 2 Remote Desktop Viewer.  Was there ever a fix found for this?  This behavior started with Wine installation / removal.

Ubuntu 10.04

---

### Post by cheyo on 2010-10-26
Thanks, it worked for me, no more duplicated wine entries.

Ubuntu 10.10 64 bit, wine 1.2

---

### Post by Mike3 on 2010-11-21
Seems to be even more duplicate entries in /usr/share/application. Tried to delete the extras. Seems to help a bit. Hopefully this helps somebody...
     By the way, just go to a terminal & type in:
```
gksu nautilus /usr/share/applications
```
     And just start deleting the duplicates. Seems to have fixed another half of the problem. You may have to reboot, though, or restart X.

---

