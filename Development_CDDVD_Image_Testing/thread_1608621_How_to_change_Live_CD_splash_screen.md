---
title: "How to change Live CD splash screen"
date: 2010-10-29
forum: Development CD/DVD Image Testing
---

### Post by jmehdi on 2010-10-29
I'm remastering the ubuntu CD, I've changed some files in the isolinux folder (access.pcx, blank.pcx, gfxboot.cfg) and I have been able to change the first screen (background color to green):

[IMG]http://img225.imageshack.us/i/1stscreen.png[/IMG] [http://img225.imageshack.us/i/1stscreen.png]("http://img225.imageshack.us/i/1stscreen.png")

But I can't change the second screen (with the "ubuntu 10.10" text)

I made my own plymouth-theme package, and removed the plymouth-theme-ubuntu-text package. But this standard ubuntu screen is still displayed.

After installation, my own plymouth theme is well displayed.

So, I'm lost, is this screen related to plymouth? (if so, how can it be displayed after removing plymouth-theme-ubuntu-text) Or is it another file/package to modify?

---

### Post by mthalis on 2010-11-03
Try this [http://uck.sourceforge.net/](http://uck.sourceforge.net/) it'll give some help

---

### Post by jmehdi on 2010-11-03
> **mthalis said:**
> Try this [http://uck.sourceforge.net/](http://uck.sourceforge.net/) it'll give some help

yep, already using it ;)

---

### Post by n~kf)}BW% on 2011-03-07
Howcome nobody knows any technical details about this "fallback" ugly plymouth screen? :S

Where is it located? How can i change it?

---

### Post by mrthing on 2011-03-09
Hello,

I too am stuck with this problem, and also would like anyone to assist in this issue.

However, as far as I have found out, I know that the kernel that boots from the live CD does not include a graphics driver as Plymouth still has issues with the Nvida Driver. Hence why your splash works fine when installed

I attempted to put a driver with the kernel but it kept panicing, so I forgot about that idea. I was a bit out of my depth.

I am looking to either change the text, or preferable have something that boots up the similar way to MoonOS (and others probably). [http://img846.imageshack.us/i/moonosbootuplivecd.png/](http://img846.imageshack.us/i/moonosbootuplivecd.png/)

Does anyone know how to do this?

---

### Post by Mallory123 on 2011-07-08
There is a fallback: usplash and/or xsplash. These should load  automatically. They do here on systems where Plymouth doesn't work.
  Plymouth requires KMS which is only available on open source drivers  (AFAIK). This means if you're running the closed ATI/Nvidia drivers,  you'll have an ugly boot experience.
  I personally just turn off quiet and splash from the kernel arguments  and watch a load of text scroll up the screen. It's only there for a  few seconds, lets me know what's going on and it doesn't waste time  loading up images.

---

### Post by KillerKink on 2011-07-21
The livecd use the plymouth from the initrd.lz. You need to modify it there.

Its took me a lot of searching to find out and thought I should share this information.

[https://wiki.ubuntu.com/CustomizeLiveInitrd](https://wiki.ubuntu.com/CustomizeLiveInitrd)

if you use uck, you can find it located in ~/tmp/remaster-iso/casper/ directory.

---

