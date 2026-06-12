---
title: "[SOLVED] Goofed up installing 8.10 last night"
date: 2008-12-08
forum: General Help
---

### Post by leveliv on 2008-12-08
alright here is what I did, I have been trying to tri boot OS X Vista and 8.10 ...so. 

I had Vista booting beside ubuntu with grub no problem..so I add OS X in the mix and it gives me the error 17 in Grub so I reinstall Ubuntu...With already have it installed so now I have two installs one on SDA5 and the other on like SDA2 ..now here's the catch, the one I boot from is the SDA2 one and the one I have all my settings and stuffed downloaded to get just "right" is on SDA5...so what I would like to do is remove that new install that I am booting grub from and use my old one..but I don't know how to change it to use the old grub

---

### Post by plucky on 2008-12-08
> **leveliv said:**
> alright here is what I did, I have been trying to tri boot OS X Vista and 8.10 ...so. 

I had Vista booting beside ubuntu with grub no problem..so I add OS X in the mix and it gives me the error 17 in Grub so I reinstall Ubuntu...With already have it installed so now I have two installs one on SDA5 and the other on like SDA2 ..now here's the catch, the one I boot from is the SDA2 one and the one I have all my settings and stuffed downloaded to get just "right" is on SDA5...so what I would like to do is remove that new install that I am booting grub from and use my old one..but I don't know how to change it to use the old grub

See this [tutorial](http://ubuntuforums.org/showthread.php?t=224351&highlight=install+grub) on howto reinstall grub to MBR.

Adjust the parameters to suit your install.

Also you might want to make a note of the latest menu.lst entries,which I assume boots the three Operating systems,so you can transfer them to the original menu.lst and enable that to boot the three OS's.


Good Luck

---

### Post by leveliv on 2008-12-11
Thanks

---

