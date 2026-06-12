---
title: "Out of range on external display with Sony Vaio laptop"
date: 2005-05-16
forum: Desktop Environments
---

### Post by rogzim on 2005-05-16
I've just installed kubuntu-5.04-install-i386.iso on my Sony Vaio laptop, everything works fine except my external display (Viewsonic VP201b) which just shows the "Out of range" message as soon as I'm in graphical mode.

In console/text mode both screens work fine. I've tried the $ sudo dpkg-reconfigure xserver-xorg command, with the right H and V sync values for my VP201b but it was useless.

It still works fine at 1600x1200 on my two displays with XP Pro, and it used to work with MDK 10.1 until I replaced this distro with Kubuntu.

What can I do to solve this problem ?

Thanks for your help.

---

### Post by agds on 2005-05-16
Here's a useful wiki you may want to read:

[http://www.ubuntulinux.org/wiki/FixVideoResolutionHowto](http://www.ubuntulinux.org/wiki/FixVideoResolutionHowto)

The instructions may not precisely address the problem you describe, but they may at least offer some hints for a remedy.

---

