---
title: "Help needed with kubuntu 64 install"
date: 2005-04-24
forum: Desktop Environments
---

### Post by crazyoldman on 2005-04-24
I want to install kubuntu 64 on a hard drive that I've previously used as a slave drive, without deleting all the data thats on it.  I've only been using it as a storage drive. When I used the live cd I could see the hard drive (unmounted) but coulddn't access it. 
How do I do the install through expert mode, without reformatting the hard drive? I need the dummies version because I really don't know what I''m doing. Ihave Windows 98se but my new system doesn't seem to be working propelry with it , so I thought I'd try Linux after a few recommendations from others.

---

### Post by Cal on 2005-04-25
I may misunderstand what you want to do, but you cannot install ubuntu without reformatting the hard drive.  You can get a copy of knoppix, run qtparted and create a second partition that you can move you data to.  Then tell kubuntu's installer to use the first partition, but thats a little dangerous.  BTW when messing with qtparted, i found it best to boot knoppix with the "linux nodma" option

P.S. I would suggest not using the 64bit version on amd64.  While the base installation is very stable and works well, you will find the user experience a little flaky as you start installing new software, at least I did on both of my machines.

---

### Post by Cal on 2005-04-25
[QUOTE=Cal]
P.S. I would suggest not using the 64bit version on amd64.  While the base installation is very stable and works well, you will find the user experience a little flaky as you start installing new software, at least I did with ubuntu (the gnome version)on both of my machines.[/QUOTE]

I should point out that I meant to suggest you use the 32 bit version, not avoid kubuntu all together.   

Good luck,

---

