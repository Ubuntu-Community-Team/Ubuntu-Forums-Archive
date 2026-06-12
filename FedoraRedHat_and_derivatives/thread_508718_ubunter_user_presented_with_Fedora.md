---
title: "ubunter user presented with Fedora"
date: 2007-07-24
forum: Fedora/RedHat and derivatives
---

### Post by S15_88 on 2007-07-24
Wasn't too sure what to title this one haha I'm a happy ubuntu user, only had minor issue with graphics card, and then a nice battle with my wifi but i got it all figured out in a jiffy.  I'm going to be taking computer science in university and i found out that the linux distro's they use in the labs are fedora.  I'm wondering what to expect when programming/doing daily activities in ubuntu then switching to fedora later that day, are there big differences i should be aware of or things like writing my programs in gedit or vi then compiling them in ubuntu then compiling them in the lab on fedora will the compiler give me errors as i know every compiler is different! and some will spit out some crazy stuff from code u thought was perfectly fine.  well if anyone wishes to give me a heads up about some key differences to watch out for between ubuntu and fedora i'd be more than happy to hear them!

Thanks, Alain

---

### Post by Rocket2DMn on 2007-07-24
As far as compiling programs go, that is just dependent on the version of the compiler they have installed - you shouldn't notice anything major since it is not so much dependend on the version of linux running.
Your other programs should also work fine, assuming they are installed.

I have Fedora Core 5 that acts as a game server.  I don't actually use the interface very much, but it is very similar to what you see in Ubuntu since it still has GNOME (or you preferred desktop manager).
You won't really notice too many differences until you start doing admininstration stuff, for example Fedora uses "yum" instead of "apt-get" and other package managers we use in Ubuntu.

---

### Post by angryfirelord on 2007-07-24
Packages - Ubuntu uses debs, Fedora uses rpms. Ubuntu uses apt-get, Fedora uses yum. Both do their jobs equally well, but apt-get works faster than rpm.
Package Updates- In Ubuntu, packages don't get version updates, only security updates. Fedora, however, gets both. Fedora is a more bleeding edge system, however many users report little problems. The thing to watch out for are kernel updates, which could screw up your wifi and force you to update/recompile the package for it. 
Security - Ubuntu lacks a firewall, but one can be added like FIrestarter. Fedora has a firewall from Red Hat and SeLinux, which is nifty tool that allows you to do some fine-tuning of security.
Speed - I found apps in Ubuntu & Debian tend to load sightly faster, but otherwise speed of apps are almost the same.

There are pros and cons to each, but both are excellent distros.

---

