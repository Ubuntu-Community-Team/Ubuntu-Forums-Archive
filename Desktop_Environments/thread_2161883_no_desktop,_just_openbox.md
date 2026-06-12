---
title: "no desktop, just openbox"
date: 2013-07-12
forum: Desktop Environments
---

### Post by schmolch on 2013-07-12
did a fresh clean install of 13.04 on my thinkpad x60t (all intel).
live-cd runs fine, install went fine.
after the first upgrade and reboot i get to the login but after that no desktop shows.
fortunately openbox is running so i at least have the menu.
if i choose lubuntu netbook from the login this works, but not the regular lubuntu.
i can see nothing wrong in dmesg, xorg.log or xsession-errors.

i guess i have to keep searching for a usable working distro, maybe something not based on ubuntu.

---

### Post by sudodus on 2013-07-12
What happens if you update and upgrade to the current versions of all packages? You can do that in the Openbox or Netbook sessions.

And then reboot ...

But I think Xubuntu 12.04.2 LTS will be a good choice until April 2015 for that computer.

---

### Post by schmolch on 2013-07-12
everything is upgraded.

---

### Post by sudodus on 2013-07-12
Your problem is unusual. The standard session is by far the most debugged one. Have you installed some particular package or PPA?

But in general, if you want a stable version for a 'production platform' rather than an 'experimental or developing platform', I suggest that you stick to the LTS versions (the current one is 12.04, and the newest point release is 12.04.2). This is what Canonical is suggesting for professional use (by companies), it will be better debugged and more polished, at least some months after the release, say after the first point release.

If you don't like Xubuntu, [LXLE]("http://www.lxle.net/") might be an alternative.

---

### Post by schmolch on 2013-07-12
I didn't install anything. I booted the live USB and did a regular install on the whole HDD. I'm trying Debian. Thx, bye.

---

### Post by RadicaX on 2013-07-12
If you did a regular install, and it worked fine at first... that does not mean it is the most up to date for things. What does not make since, is that it works from the LiveUSB, but does not once installed. Since you are trying Debian, I guess we will not find out now. Now I have been looking it up, the thinkpad x60t, all I find is an older type computer. Perhaps you need a Linux more geared for accepting use of older hardware? (Lubuntu is amazing, and can run on very minimal power, but that does not mean it is made for older hardware quite.) You might look into it a bit more. It is also to note, it does work on the notebook DE, (because it is a laptop/notebook right?) So it might not work on normal Lubuntu.

---

### Post by schmolch on 2013-07-13
> **RadicaX said:**
> If you did a regular install, and it worked fine at first... that does not mean it is the most up to date for things. 

it is obviously as old as the release, that's why i updated it.

> 
What does not make since, is that it works from the LiveUSB, but does not once installed. Since you are trying Debian, I guess we will not find out now. Now I have been looking it up, the thinkpad x60t, all I find is an older type computer. Perhaps you need a Linux more geared for accepting use of older hardware? (Lubuntu is amazing, and can run on very minimal power, but that does not mean it is made for older hardware quite.) You might look into it a bit more.

It is a core-duo with 3gb ram. lubuntu runs on a 486, just slower. speed is irrelevant as long as the hardware is supported and it definately is (they dropped 386 support just a few months ago in the kernel).

>  It is also to note, it does work on the notebook DE, (because it is a laptop/notebook right?) So it might not work on normal Lubuntu.

lubuntu supports laptops as well, even if you want to run the desktop-version. I know it is preposterous to run a desktop on a laptop but they say it can be done.

I installed debian-mint on it and it works fine, even with lxde, so everything is good.

---

### Post by RadicaX on 2013-07-20
Well, good to hear you have something running now. Sorry you could not get Ubuntu up and running on it. I just wonder what it could have been. Either way, am glad you have Linux!

---

