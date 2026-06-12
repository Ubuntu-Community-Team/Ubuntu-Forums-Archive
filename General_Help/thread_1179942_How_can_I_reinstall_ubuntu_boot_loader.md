---
title: "How can I reinstall ubuntu boot loader?"
date: 2009-06-06
forum: General Help
---

### Post by colau on 2009-06-06
Hi,
After installing kubuntu the kubuntu boot loader is installed.
How can I get the ubuntu boot loader installed again?
I tried this running a live cd of ubuntu 9.04.
```

find /boot/grub/stage1

```
But can't find anything:).

---

### Post by Legace on 2009-06-06
# Boot your computer up with Ubuntu CD
# Open a terminal window or switch to a tty.
# Go SuperUser (that is, type "sudo -s"). Enter root passwords as necessary.
# Type "grub"
# Type "find /boot/grub/stage1". You'll get a response like "(hd0,1)". Use whatever your computer spits out for the following lines.
# Type "root (hd0,1)", or whatever your hard disk + boot partition numbers are for Ubuntu.
# Type "setup (hd0)", to install GRUB to MBR, or "setup (hd0,1)" or whatever your hard disk + partition nr is, to install GRUB to a partition.
# Quit grub by typing "quit".
# Reboot and remove the bootable CD.

---

### Post by colau on 2009-06-06
> **Legace said:**
> # Boot your computer up with Ubuntu CD
# Open a terminal window or switch to a tty.
# Go SuperUser (that is, type "sudo -s"). Enter root passwords as necessary.
# Type "grub"
# Type "find /boot/grub/stage1". You'll get a response like "(hd0,1)". Use whatever your computer spits out for the following lines.
# Type "root (hd0,1)", or whatever your hard disk + boot partition numbers are for Ubuntu.
# Type "setup (hd0)", to install GRUB to MBR, or "setup (hd0,1)" or whatever your hard disk + partition nr is, to install GRUB to a partition.
# Quit grub by typing "quit".
# Reboot and remove the bootable CD.
Thanks for your quick reply.
```

# Type "grub"

```
Do I have to type the double quote ("") as well?

---

### Post by Legace on 2009-06-06
No.

---

### Post by colau on 2009-06-06
> **Legace said:**
> No.
Thank for your reply and for changing your avatar:D

---

### Post by Legace on 2009-06-06
> **colau said:**
> Thank for your reply and for changing your avatar:D

So it worked?

(Why are you thanking me for changing my avatar :P?)

---

### Post by Sidewinder1 on 2009-06-06
(Why are you thanking me for changing my avatar :razz:?)

{I was wondering that as well...} :-)

---

### Post by colau on 2009-06-06
> **Legace said:**
> So it worked?

(Why are you thanking me for changing my avatar :P?)
Yes,it worked.
(Your previous avatar was nothing but a rectangle shape saying "Legace's avatar"):D

(Now there is a picture at left);)
Anyway thanks for your reply.

---

