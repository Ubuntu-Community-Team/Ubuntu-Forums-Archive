---
title: "tweaking graphics card in edgy"
date: 2006-12-26
forum: Gaming &amp; Leisure
---

### Post by zedd2006 on 2006-12-26
ok i finally got doom3 working, and the graphics, i have 3d acceraltion, but its choppy on everything, is there anything i can do to fix this? im running a p4 3ghz HT with 1.5gb of ram, and a ati radeon x300 128mb pci-e video card, in windows i could play this game at 1024x768 all maxed and it ran fine.

any help would be great, if not thanks for looking anyway.

---

### Post by Kubunteando on 2006-12-26
What version of the ATI drivers are you using?

Can you have a look at:

[http://www.gentoo.org/doc/en/dri-howto.xml](http://www.gentoo.org/doc/en/dri-howto.xml)

Specially the step 6.

The Fast Writes crahes my system. Maybe you are more lucky.
But the "PageFlip" increased the performance.
This page is for the Open Source DRI drivers, but you can give a try.
Make a backup of the xorg.conf file first so you can restore it if you are not happy.

Can you check what is the memory consumption when you are playing?
Is it using the swap memory heavily?

---

### Post by smartbei on 2006-12-26
If you haven't yet, install the ATI binary driver - the preformance is better.
[http://ubuntuforums.org/showthread.php?t=204910](http://ubuntuforums.org/showthread.php?t=204910)

---

