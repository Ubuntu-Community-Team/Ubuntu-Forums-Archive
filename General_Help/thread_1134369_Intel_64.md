---
title: "Intel 64"
date: 2009-04-23
forum: General Help
---

### Post by SportsGuy2 on 2009-04-23
I was wondering if I need to download the 32 bit or 64 for my processor. Here's what I have now:


"Intel® Core™ 2 Quad processor Q9550 (12MB L2, 2.83GHz, 1333FSB)
Genuine Windows Vista® Home Premium Edition SP1, 64-Bit"

---

### Post by codeseer on 2009-04-23
64-bit.

---

### Post by SportsGuy2 on 2009-04-23
okay thanks. and another question, when i partition and install it with a bootloader, the default os will still be windows, correct?

---

### Post by dabl on 2009-04-23
> **SportsGuy2 said:**
> okay thanks. and another question, when i partition and install it with a bootloader, the default os will still be windows, correct?

Nope.  The default installation includes installing Grub in the MBR of the first hard drive, and setting Windows as the "Other OS".  *buntu will be the default OS.  You can (with knowledge and research) edit the menu.lst file and change the boot sequence, but that is another topic.

---

### Post by codeseer on 2009-04-23
You can specify the default OS to boot by editing the 'default' option in the /boot/grub/menu.lst file.

---

### Post by SportsGuy2 on 2009-04-23
> **codeseer said:**
> You can specify the default OS to boot by editing the 'default' option in the /boot/grub/menu.lst file.

how do i do this? (sorry I'm sorta new)

---

### Post by codeseer on 2009-04-23
> **SportsGuy2 said:**
> how do i do this? (sorry I'm sorta new)

Open a terminal (Applications->Accessories->Terminal), once Ubuntu is installed. Then type the following:

```
gksudo gedit /boot/grub/menu.lst
```

You will see something like this in the file:

```

## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.
# WARNING: If you are using dmraid do not use 'savedefault' or your
# array will desync and will not let you boot your system.
**default		0**

```

The number to change it to depends on how many menu entries you have; your windows entry will most likely be 5 though. After making the change to the number, hit the Save button and close out and then reboot to make sure it works as intended.

You may also edit the 'timeout' option to fit your needs:

```

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
**timeout		4**

```

---

### Post by SportsGuy2 on 2009-04-23
okay ill do that. thanks a ton!

---

### Post by SportsGuy2 on 2009-04-25
okay, thanks alot, it worked. (i forget how to put the solved prefix)

---

