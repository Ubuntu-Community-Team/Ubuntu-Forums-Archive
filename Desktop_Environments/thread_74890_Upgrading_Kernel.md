---
title: "Upgrading Kernel?"
date: 2005-10-12
forum: Desktop Environments
---

### Post by bugmenot on 2005-10-12
Hi, I'm new and I need to upgrade my kernel to 2.6.13.2. How do I do that? I have both the patch-2.6.13.2.bz2 and the 2.6.13.2.tar.gz (gz i think, maybe a different extantion). I need it to install [http://users.pandora.be/seppe/nitro/2.6.13.2-nitro1/series](http://users.pandora.be/seppe/nitro/2.6.13.2-nitro1/series) but I don't know how to install the 2.6.13.2 like I said. Please help me, those jerks at IRC don't help at all and just question me

---

### Post by matthew on 2005-10-12
Look at this  [http://www.ubuntuforums.org/showthread.php?t=56835](http://www.ubuntuforums.org/showthread.php?t=56835)

---

### Post by bugmenot on 2005-10-12
Yeah I was there but it didn't help me on upgrading

---

### Post by matthew on 2005-10-12
Did you try this? It was at the bottom of the page you linked to.

```
**(HOW TO INSTALL)**
Since there is no ebuild, here is how you can install nitro-sources manually: 
1. Download linux-2.6.13.2-nitro1.bz2
2. Download Linux 2.6.13.2 from http://kernel.org
3. Extract linux-2.6.13.2.bz2 to /usr/src
4. cd /usr/src
5. mv linux-2.6.13.2 linux-2.6.13.2-nitro1
6. cd linux-2.6.13.2-nitro1
7. bzcat /path/to/linux-2.6.13-nitro1.bz2 | patch -p1
8. cp /usr/src/linux/.config /usr/src/linux-2.6.13.2-nitro1
9. rm linux
10. ln -sf linux-2.6.13.2-nitro1 linux
11. cd linux
12. make oldconfig
13. make && make modules_install
14. mount /boot (if it's on a seperate partition)
15. cp arch/i386/boot/bzImage /boot/nitro-sources
16. add entry in your boot manager which points to /boot/nitro-sources image
(for grub: take a look in /boot/grub/menu.lst)
17. reboot and behold!
```

---

### Post by wylfing on 2005-10-12
Hold on! Why do you need to upgrade your kernel? This isn't something that should be taken lightly (even though it *is* taken lightly by most Ubuntu users). Either the Ubuntu updater is telling you to upgrade, or else you probably should not be upgrading. What's going on?

---

### Post by matthew on 2005-10-13
[quote=wylfing]Hold on! Why do you need to upgrade your kernel? This isn't something that should be taken lightly (even though it *is* taken lightly by most Ubuntu users). Either the Ubuntu updater is telling you to upgrade, or else you probably should not be upgrading. What's going on?[/quote] I read through the page he linked to. Apparently he wants to use this special "whiz-bang" experimental kernel with low latency...my guess is for playing games or doing something with audio-visual recording or editing. It's being put out by some Gentoo developers so I was seriously thinking of pointing him to them for help but I thought I would give him what I could from here first. Anyway, I didn't pursue the matter much since he was pretty surly in that last sentence of his original post and I didn't think he was likely to respond well to a request for more information so we could give him some real assistance reaching whatever his ultimate goal is. He feels he knows how to get where he wants to go--he just needs this special kernel. :)
[quote=bugmenot]Please help me, those jerks at IRC don't help at all and just question me[/quote] Sounds like he isn't likely to want the help you are offering wylfing (and I would agree he likely needs) so I thought I would just point him at the directions he must have failed to notice and leave him to it.

---

### Post by wylfing on 2005-10-13
Amen.

This looks closed, then, as far as I can see.

---

