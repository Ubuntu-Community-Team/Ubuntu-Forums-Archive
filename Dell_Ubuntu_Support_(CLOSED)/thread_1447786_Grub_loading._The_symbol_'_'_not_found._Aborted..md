---
title: "Grub loading. The symbol ' ' not found. Aborted."
date: 2010-04-05
forum: Dell Ubuntu Support (CLOSED)
---

### Post by merry_meerkat on 2010-04-05
This is an occurrence of [bug #482757]("https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/482757"). I've just wasted a day solving this, so I am posting here in the hope that it'll save others the hassle.

On a Dell machine, the included software **Dell DataSafe Local Backup** (DDSLB) seems to mess up GRUB. When that happens, booting results in GRUB showing the following error message:

```
Grub loading. The symbol '*X*' not found. Aborted.
```
And for *X* above, a random string of characters is displayed.

The only fix I have found is the following:
1. **re-install GRUB from a live CD** to be able to boot up again
2. boot into Windows and **uninstall DDSLB**
... this will once again have messed up GRUB
3. **re-install once again GRUB from a live CD**. That solved it for me.

To do steps 1 and 3, i.e. re-installing GRUB from a live CD, the method 3 described here worked fine for me:
[https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202]("https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202")
Note only "METHOD 3 - CHROOT" for re-installing GRUB worked for me. Find it on the aforementioned page.

(I'm on a Dell Studio 1747, with Karmic as well as Win 7 home pro)

---

### Post by drs305 on 2010-04-05
Thanks for sharing this. I'll put it in the troubleshooting section of my Grub 2 Basics thread and link this post.

---

### Post by merry_meerkat on 2010-04-05
I should have added that this (obviously) only applies to dual-boot machines with Dell's software. And perhaps only to Windows 7 (though I cannot verify the latter).

---

### Post by mbickell on 2010-04-08
Thank you for this post, I have been struggling with this for a few days now.

But, of course, Murphy's Law had to rear it's ugly head. When I try to uninstall DDSLB in "Programs and Features" I got an error that looked like the attached .bmp image.
I can't believe it! A simple thing like uninstalling a program and something has to go wrong!
So, I realise that this is probably the wrong place to post this, but I just had to try my luck. If anyone has any ideas, please help. (I'm busy trying to get support from dell)

---

### Post by merry_meerkat on 2010-04-09
Sorry, no idea. Om my machine it uninstalled without hitch. Probably best to look on Dell and Windows related fora for help - and ask Dell support. But you're doing that already...

---

### Post by karasuman on 2010-04-10
Same problem here.  I thought I had just messed something up.

---

### Post by icedecker on 2010-05-10
To remove the Dell Data Safe, it is recommended to start the Windows in the safe mode (pressing key F8 repeatedly when the pc is initializing), and go to uninstall it.

---

### Post by MattBD on 2010-07-14
I've had this issue, so I'm very pleased to see a potential solution.
I have a Dell Studio which dual-boots Windows 7 and Ubuntu Lucid, and a Mini Inspiron which dual-boots XP and Ubuntu Netbook Edition, and I have only had this issue on the Studio, although both have the Dell Data Safe software, so it could well be Win 7 specific.

---

### Post by Selgar on 2010-11-27
I've just uninstalled Dell data safe backup without a hitch on my Dell Inspiron [FONT=Nimbus Roman No9 L]M5030[/FONT] and Grub works smoothly without corrupting when I boot into either Windows 7 or Ubuntu 10.04.

Thanks merry_meerkat!   :)

---

