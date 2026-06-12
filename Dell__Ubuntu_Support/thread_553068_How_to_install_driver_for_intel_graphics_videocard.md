---
title: "How to install driver for intel graphics videocard to get Beryl?"
date: 2007-09-17
forum: Dell  Ubuntu Support
---

### Post by kazuya on 2007-09-17
How to install driver for intel graphics videocard?
I have followed the guide sort of. My concern is that even after installing the intel video driver from synaptic or via apt-get, how do I configure xorg such that I can use or do Beryl or compiz?

I have a 2004 Dell Desktop with intel graphics video card. I know it is neither ati nor nvidia? I see already installed drivers for 740 and 810. What do I do to xorg config file to get the driver really working.?

With nvidia card, I could simply use envy to do all the setup. But there is nothing in place for intel videocard.

Anyone using intel videocard in linux with any ideas?

---

### Post by JBAlaska on 2007-09-17
Are you using feisty, if so try enabling desktop effects. On my backup dell with Intel 810 integrated video it worked out of the box, if desktop effects works (wobbly windows and 3d cube) you can simply uninstall the limited compiz and reinstall the full version.

You might not have to mess with xorg.conf at all if your lucky.

---

### Post by notwen on 2007-09-17
Which model of a Dell laptop do you have?  (Latitude, Inspiron, etc) Can't recall this will work, but try typing this into a terminal and copy/pasting the output back here.

```
lspci -v | grep Graphics
```

Hopefully this will help us identify your Graphics card. =]

---

### Post by kazuya on 2007-09-17
thnaks guys. I'll test it out when I get back. I think I have the videocard driver somewhat installed from synaptic. I updated the kernel and then reinstalled the intel 810 driver.. It seems to work, but how do I know if the videocard driver is really properly installed and optimized for full use versus  not. I fear the xorg conf file may need some more things enabled like compositing.., etc.. for Beryl or fusion to work...

Any ideas? I'll post back later when I get home tonight.

The machine is running Feisty.

---

### Post by kazuya on 2007-09-17
lspci -v | grep Graphics
00:02.0 VGA compatible controller: Intel Corporation 82865G Integrated Graphics Controller (rev 02) (prog-if 00 [VGA])
kazuya@kazuya-desktop:~$

---

### Post by notwen on 2007-09-18
That's not giving me quite what is needed to determine your Graphics chipset.  Do you know what model of the Dell laptop this is?  Unless it is just terribly an out-of-date chipset, seems like the majority of Intel graphics support atleast some of the less strenuous effects of Beryl/Compiz.  I have a Inspiron 1420n with the Intel X3100 chipset and I am running Beryl w/ zero issues.

---

### Post by girishkolari on 2007-09-19
I too have same problem,
I am using Dell Inspiron 640m.
Can I find some help?

---

### Post by notwen on 2007-09-20
The 640m has the Intel 950 chipset, you should be able to use the driver on this [thread]("http://ubuntuforums.org/showthread.php?t=494943"). =]

---

### Post by girishkolari on 2007-09-20
thanks for some for link, i would follow with link....

---

### Post by kazuya on 2007-09-24
Thanks as well. I know it would work now. I would say solved, but I have to test it out. I know it works with Zenwalk, and should with this as well..
EDIT: I am now running Linux Mint 3.1 Celena. Drivers wree installed automatically without me. Beryl worked the moment I tested it. Great work.

---

