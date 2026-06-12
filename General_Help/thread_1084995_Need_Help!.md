---
title: "Need Help!"
date: 2009-03-02
forum: General Help
---

### Post by HotDrive on 2009-03-02
Hi all.

Need help trying to understand a problem.
Today, I started my PC and no Ubuntu image on Grub(!). Only Memtest and Windows XP. Seems all the files are still in Ubuntu partition, but image disappeared. Had 2.6.27-12 installed.
Can I install it again without loosing data? How?
Is it possible to install any other image (like 8.04 LTS, from CD) and keep settings?
Really need help with this one :confused:

Thanks all!

---

### Post by zvacet on 2009-03-03
If you want to keep your data then you need separate home partition.if you don´t have one follow [this guide.]("http://psychocats.s465.sureserver.com/ubuntu/separatehome")When you are finish you can reinstall but **don´t format home partition** during install.

---

### Post by HotDrive on 2009-03-03
Thanks for your reply.
I've checked the procedure and seems that it works for changing ubuntu files from one partition to another. My problem is that appears that no image is in my first partition. How can I get it back there? I just need an image in the disk so that I can reconfigure grub to recognize it an boot there!

---

### Post by 4Orbs on 2009-03-03
Maybe you only scrolled down the grub list and hid the top entries for Ubuntu?

---

### Post by HotDrive on 2009-03-04
Checked That...
No image on disk. My Grub only used to have 4 entries:
- Ubuntu
- Ubuntu (recovery)
- Memtest
- Windows XP

Now, it has:

- Memtest
- Windows XP

I've checked the /boot directory and there is no image there!

---

