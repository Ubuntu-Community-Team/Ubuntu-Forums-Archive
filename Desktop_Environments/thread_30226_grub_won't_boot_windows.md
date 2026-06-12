---
title: "grub won't boot windows"
date: 2005-04-27
forum: Desktop Environments
---

### Post by klutzini on 2005-04-27
Hi all,

I have 2 hard drives in my amd x64 machine, hda1 is winxp (for clients that send me windoze files!!) and hdd for kubuntu.

When I boot up I get grub, then booting ubuntu is not a problem, but when I choose winxp (which kubuntu found) I get loaded into grub. But then what do I do to load windows? ](*,) 

Below is part of my menu.1st

# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hda1
title		Microsoft Windows XP Home Edition
root		(hd0,0)
savedefault
makeactive
chainloader	+1

Hope you can help....

Cheers...

---

### Post by MetalMusicAddict on 2005-04-27
Try setting the "Access Mode" for the HDs in the BIOS to "LBA" (Large Block Addressing).

---

### Post by klutzini on 2005-04-27
Just had a look in my bios.

It says that it is already set to auto, the other option is disable.

---

### Post by thecrimsonking on 2005-04-27
Did you install Grub on hdd, or did you install it on the MBR on hda1?

---

### Post by klutzini on 2005-04-28
can't remember. How do I find out? (oh.. and simple text and pics help!!) :grin:

---

### Post by klutzini on 2005-05-03
In the end what I did was to reformat both drives and start again... now I can boot up Kubuntu and Windoze (if I must!!).

---

