---
title: "nouveau problems"
date: 2016-09-14
forum: Desktop Environments
---

### Post by pattylad on 2016-09-14
Successfully installed and dual booting Ubuntu 16.04 LTS alongside Windows 10 but a few lingering problems:

1) Windows will not recognize the Ubuntu partition and skips the selection screen on startup for choosing the OS I want to use (by far the lesser of two evils)

2) When I choose to boot Ubuntu I have to edit the boot command in grub2 by adding "nouveau.modeset=0" to the end of the line beginning with "linux" every time or the computer freezes. From what I'm given to understand this has something to do with the Nvidia driver in the new computer I'm trying to work with (an MSI with an Nvidia GTX960M). I tried to boot using the nomodeset parameter as well as removing the drivers and reinstalling them but to no avail. Any help would be greatly appreciated.

---

### Post by &amp;KyT$0P# on 2016-09-14
> **pattylad said:**
> 2) When I choose to boot Ubuntu I have to edit the boot command in grub2 by adding "nouveau.modeset=0" to the end of the line beginning with "linux" every time or the computer freezes. From what I'm given to understand this has something to do with the Nvidia driver in the new computer I'm trying to work with (an MSI with an Nvidia GTX960M). I tried to boot using the nomodeset parameter as well as removing the drivers and reinstalling them but to no avail. Any help would be greatly appreciated.
Not sure if this is what you're looking for or not, but you can make that change "permanent".
Edit [FONT=Courier New]/etc/default/grub[/FONT] as root, edit the [FONT=Courier New]GRUB_CMDLINE_LINUX_DEFAULT[/FONT] line to include it.  For example, if you have "splash" listed there already, you'd change it to this -
```
GRUB_CMDLINE_LINUX_DEFAULT="splash nouveau.modeset=0"
```

Then run [FONT=Courier New]sudo update-grub[/FONT] to save the changes to GRUB.

Does that useful for you?

---

### Post by Bucky Ball on 2016-09-15
> **pattylad said:**
> 1) Windows will not recognize the Ubuntu partition and skips the selection screen on startup for choosing the OS I want to use (by far the lesser of two evils)

Excuse my ignorance, but how are you then booting into Ubuntu? :-k

The next bit of your post goes on to describe selecting Ubuntu from the grub and changing the kernel line ...

---

