---
title: "Uninstalled Ubuntu Partition, can't get into windows..."
date: 2009-04-04
forum: General Help
---

### Post by Rlad78 on 2009-04-04
I decided to reformat my computer so I deleted the Ubuntu partition first. Unfortunately, I was not able (for some strange reason) reformat windows. I restarted my computer so I could go into safe mode, but the Boot GRUB loader came up with Error 22.

I then proceeded to put in the windows disk and reformat it.
It's currently reformatting, but I have a feeling that the GRUB loader is still going to be there.

What can I do to get rid of it besides reinstalling Ubuntu?

---

### Post by mike555 on 2009-04-04
You can use a live ubuntu cd and type;

 dd if=/dev/zero of=/dev/hda bs=512 count=1

That will erase any MBR. If your drive is not /dev/hda then please use
the proper one (such as /dev/hde or /dev/sda or what have you)

== of course after doing this nothing will boot, so you will need to reinstall ==

---

### Post by zvacet on 2009-04-04
I don´t know if I understand you right,but if you have Windows installed and you can boot in it then do [this]("http://www.users.bigpond.net.au/hermanzone/p18.htm#MbrFix.exe") and you will have Windows bootloader again.

---

