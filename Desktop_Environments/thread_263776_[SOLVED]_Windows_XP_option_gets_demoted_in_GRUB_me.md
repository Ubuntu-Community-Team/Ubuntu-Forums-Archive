---
title: "[SOLVED] Windows XP option gets demoted in GRUB menu after kernel update."
date: 2006-09-23
forum: Desktop Environments
---

### Post by chrismyers on 2006-09-23
HI Guys,

Anyone know how to make a default menu.lst boot option stay static even if after a kernel update?

I'm in the process of persuading a friend to use Ubuntu, but he wants WindowsXP as his default option. He complained that after he does an update the latest Ubuntu kernel hogs the default option.

Even though I prefer Ubuntu as my default, I have to agree with my friend that it's a bit rude of Ubuntu to steal the limelight. He said that that seems more like Windows behaviour than Ubuntu. :oops: 

Any help would be appreciated. Who know's, he may even drop Windows if he sticks with Ubuntu long enough!

---

### Post by hayalci on 2006-09-23
You may put windows option before ```
### BEGIN AUTOMAGIC KERNELS LIST

``` lines in menu.lst, then change the line ```
default 0
```.

This way, windows option will remain after Ubuntu updates and it will stay as the default one.

---

### Post by KStorm on 2006-09-23
Change the value of "default" so it corresponds to the matching GRUB menu entry, keeping in mind that the numbering starts with zero.  So if you have three Ubuntu entries (main os, recovery, mem test), a "Other Operating Systems" entry, and two XP entries (for 'recovery' and the OS itself), you would set 'default' to 5.

Believe it or not, the "Other Operating Systems" is actually something you can choose if you set the 'default' to 4.

---

### Post by AClx on 2006-09-23
To elaborate on what hayalci said... the link that explains how to do it is here:
[https://help.ubuntu.com/community/GrubHowto#head-92178081fe4541430c264adfedcca91f4f920512]("https://help.ubuntu.com/community/GrubHowto#head-92178081fe4541430c264adfedcca91f4f920512")

> Ubuntu uses a tool called update-grub to modify menu.lst. It automatically detects all of the kernels you have in the /boot directory, and applies various global settings to each one. Whenever you install kernel updates from the repositories, update-grub is run to update the grub settings.

So edit menu.lst and you should see this:
> ### BEGIN AUTOMAGIC KERNELS LIST
followed by probably a bunch of comments, some boot options, and a list of a few Ubuntu kernels.
and then later, you'll see this:
> ### END DEBIAN AUTOMAGIC KERNELS LIST

What you need to do is move the Windows boot option before the beginning of the first line, or after the end of the second line. Outside of the "Automatgic Kernels List" section, the kernel upgrade procedure won't modify the file. When you move the option for Windows, you will of course change the order of the boot options. So adjust what you have for "default" accordingly - i.e. recount the order of the options again. To make it simple, since your friend wants Windows as the default, follow hayalci's instructions to make windows the first option and set > default 0

---

### Post by chrismyers on 2006-09-24
Thanks guys.

Just what I needed. The fantastic forums are why I'm sticking with Ubuntu. :D

---

