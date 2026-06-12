---
title: "How to edit Grub loader"
date: 2009-04-18
forum: General Help
---

### Post by oldtraveler on 2009-04-18
On my laptop which has XP Home I just installed Ubuntu 8.10 on a new separate partition.  Now upon booting it shows the boot loader as well as the Windows OS, but I wish to change the time to default as well as the default OS for booting.

How? I can't seem to locate a file called Grub.

---

### Post by redbook4574 on 2009-04-18
> **oldtraveler said:**
> On my laptop which has XP Home I just installed Ubuntu 8.10 on a new separate partition.  Now upon booting it shows the boot loader as well as the Windows OS, but I wish to change the time to default as well as the default OS for booting.

How? I can't seem to locate a file called Grub.

Get kgrubeditor from synaptic it will allow you to edit grub graphically.

---

### Post by oldtraveler on 2009-04-18
Thank you ,Redbook.

I figured there was an easy answer and you had it.

---

### Post by Ticketoride on 2009-04-18
> **redbook4574 said:**
> Get kgrubeditor from synaptic it will allow you to edit grub graphically.
Unfortunately it doesn't seem to load in Jaunty 9.04. Truly a Shame.

---

### Post by SpinningAround on 2009-04-18
Can't you simply edit /boot/grup/menu.lst?

---

### Post by -kg- on 2009-04-18
> **SpinningAround said:**
> Can't you simply edit /boot/grup/menu.lst?

Yes, you should be able to:

```
gksu gedit /boot/grub/menu.lst
```

(Of course, assuming that Jaunty still has gedit...if not, any text editor will do)

If you need help with the actual editing, just post back. Oh, and I probably don't have to remind you to make a backup copy of your original menu.lst file, just in case, right? ;)

---

