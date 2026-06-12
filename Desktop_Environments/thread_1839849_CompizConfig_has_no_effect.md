---
title: "CompizConfig has no effect"
date: 2011-09-06
forum: Desktop Environments
---

### Post by senserbase on 2011-09-06
hello all ` 

as i was saying the CompizConfig has no effect , i can't use the shift+ctrl+[right numpad] combo , switching desktop environments is only by right to left and not right-left-up-down , pushing a windows to the end of the screen doesn't make him get "autoshaped to the dir" --- and basically all the features of the compizconfig doesn't seem to work --- ohh and the most irritating thing is that the left panel is always showing even in  full windows (it only disappears when a video is on full screen)

p.s I already tried to reinstall the two compozconfig that I found in “Ubuntu software manager” 

please help ! 

Thanks for all the helpers ! :)

---

### Post by 3Miro on 2011-09-06
If CCSM isn't working, it means that Compiz isn't working.

1. Which version of Ubuntu is this?
2. Are you using Gnome interface or Unity interface (2D/3D)?

It sounds like you hare using Unity 2D, if you logout you should be able to select Ubuntu or Ubuntu Classic or Ubuntu Classis (No Effects) or Unity 2D. The first two use Compiz and you can adjust effects with CCSM.

---

### Post by CharlesA on 2011-09-06
Other thread is [here]("http://ubuntuforums.org/showthread.php?p=11214140#post11214140").

---

### Post by 3Miro on 2011-09-06
> **CharlesA said:**
> Other thread is [here]("http://ubuntuforums.org/showthread.php?p=11214140#post11214140").

senserbase, Unity 2D is still not "officially" released and it is somewhat lacking (what you have is more or less a test version). You cannot adjust Unity 2D from within CCSM and I don't know if you can customize Unity 2D at all.

You should be able to run classic Gnome and that has some customizations on Metacity (System -> Prefs -> Keyboard Shortcuts).

---

### Post by senserbase on 2011-09-07
> **3Miro said:**
> If CCSM isn't working, it means that Compiz isn't working.

1. Which version of Ubuntu is this?
2. Are you using Gnome interface or Unity interface (2D/3D)?

It sounds like you hare using Unity 2D, if you logout you should be able to select Ubuntu or Ubuntu Classic or Ubuntu Classis (No Effects) or Unity 2D. The first two use Compiz and you can adjust effects with CCSM.

1.11.04 -updated
2.i have  the untity 2d interface ,but even with or without it (classic , and the only `ubuntu` one ) i still have this problem ... please help , i just cant stand this - not having all the windows controling options

---

### Post by senserbase on 2011-09-08
please help

---

### Post by senserbase on 2011-09-09
someone please , any thing!

---

### Post by jmate24 on 2011-09-09
enabling compiz crashes unity and makes the system unusable. don't enable it and if you are using an intel card i am assuming that you have a laptop? is that correct because if not then try to upgrade your videocard.

---

### Post by senserbase on 2011-09-11
> **jmate24 said:**
> enabling compiz crashes unity and makes the system unusable. don't enable it and if you are using an intel card i am assuming that you have a laptop? is that correct because if not then try to upgrade your videocard.

no - for the laptop ;

i really cant find any fix in the Internet for my situation ..

so maybe someone know how to re-install ubuntu only by deleting and installing the system files (-ubuntu) without my personal files (i use windows 7 along side ubuntu 11.04 and I have files in the ubuntu side too ) ?
 
and maybe someone know when the new ubuntu (11.10) comes out ?

---

### Post by Krytarik on 2011-09-11
> **senserbase said:**
> 
i really cant find any fix in the Internet for my situation ..
Taking the name of your video card from your [other thread]("http://ubuntuforums.org/showthread.php?t=1832912"), Nvidia GeForce 7300 GT, I think the GT version of the 7300 series might be blacklisted, too. Or at least not - or just not considered - capable to run Unity and Compiz  with the drivers you tried. Please see this recent thread for possible fixes:

[http://ubuntuforums.org/showthread.php?t=1842210](http://ubuntuforums.org/showthread.php?t=1842210)

> **senserbase said:**
> 
so maybe someone know how to re-install ubuntu only by deleting and installing the system files (-ubuntu) without my personal files (i use windows 7 along side ubuntu 11.04 and I have files in the ubuntu side too ) ?
Yeah. you could just backup your home directory, "/home/USERNAME", to another drive/partition, and restore it after the installation. But to preserve the permissions/ownership of the files/dirs, the backup location should possibly be Linux formatted as well.

> **senserbase said:**
> 
and maybe someone know when the new ubuntu (11.10) comes out ?
Release Schedule: [https://wiki.ubuntu.com/OneiricReleaseSchedule](https://wiki.ubuntu.com/OneiricReleaseSchedule)

Current Images: [http://releases.ubuntu.com/oneiric/](http://releases.ubuntu.com/oneiric/)

Greetings.

---

### Post by MG&amp;TL on 2011-09-11
Two things:

For reliable compiz, use a pre-unity release. (10.10 and earlier)

Ubuntu 11.10 comes out in October, but you can grab (a slightly unstable) version now.

---

### Post by senserbase on 2011-09-12
> **Krytarik said:**
> Taking the name of your video card from your [other thread]("http://ubuntuforums.org/showthread.php?t=1832912"), Nvidia GeForce 7300 GT, I think the GT version of the 7300 series might be blacklisted, too. Or at least not - or just not considered - capable to run Unity and Compiz  with the drivers you tried. Please see this recent thread for possible fixes:

[http://ubuntuforums.org/showthread.php?t=1842210](http://ubuntuforums.org/showthread.php?t=1842210)


Yeah. you could just backup your home directory, "/home/USERNAME", to another drive/partition, and restore it after the installation. But to preserve the permissions/ownership of the files/dirs, the backup location should possibly be Linux formatted as well.


Release Schedule: [https://wiki.ubuntu.com/OneiricReleaseSchedule](https://wiki.ubuntu.com/OneiricReleaseSchedule)

Current Images: [http://releases.ubuntu.com/oneiric/](http://releases.ubuntu.com/oneiric/)

Greetings.


i use a built in intel gc...

the thing is that everything worked great until one day i tried to test my "not-working" nvidia 7300gt gc - i succeed booting with it in failsafe graphic mode - (but i dont use it anymore) ... so now when i am booting my ubuntu with my working intel built in gc i have those problem - > i cant do the ctrl+alt+s combo and almost every thing including the quick terminal key combo (the only thing i can do is the quick show desktop key combo ) and now i even cant go back to my unity "theme" in ubuntu (it saying that i have a problem) something that i never had -- basically i just have like windows 98 classic with ubutnu classic skin - i cant do anything advanced with my GUI

so again how i reinstall my ubuntu - just backup my files to lets say in windows pattern and delete all the linux pattern -> too bad there is no like reinstall ubuntu system files (like windows )

thanks for the helpers

---

### Post by senserbase on 2011-09-13
please answer

---

### Post by Krytarik on 2011-09-13
> **senserbase said:**
> please answer
Oh, I thought you already got this:
> **Krytarik said:**
> Yeah. you could just backup your home directory, "/home/USERNAME", to  another drive/partition, and restore it after the installation. But to  preserve the permissions/ownership of the files/dirs, the backup  location should possibly be Linux formatted as well.
Sorry, man! Considering your set of issues, I really think it's the best to just reinstall.

---

### Post by Blasphemist on 2011-09-13
Do I understand correctly that you have both the built in Intel gpu and an nvidia? If so this is sometimes referred to as switchable graphics. There is an ongoing project called debumblebee on this. [https://github.com/z0rc/debumblebee](https://github.com/z0rc/debumblebee) 

I've run into this working with others but haven't fully investigated. This link does give you a link to installation help and provides description in the readme.

---

