---
title: "Please, help me choose another distro"
date: 2006-08-24
forum: Desktop Environments
---

### Post by ThirdWorld on 2006-08-24
Please i need to choose another distro. in ubuntu my video card (Rage 128 Pro Ultra) doesnt work. No video aceleration and no way to play old games that are available in the repositories like hexen, quake 2 etc. I have asked many times how to install xfree86 but looks likes no one knows or probably the people who knows are not available. So guys which will be a good distro that could support xfree86? opensuse? freespire? fedora?

Thanks

---

### Post by llamakc on 2006-08-24
Debian Potato.

---

### Post by cmost on 2006-08-24
For excellent hardware detection and automatic compilation of video, wireless and other drivers via dkms please see PCLinuxOS.  A new version has recently been released; in three flavors depending on your needs:  MiniME (minimalistic), Junior (one best app for most common needs), and Big Daddy (full enchelada.)  You can get more details here:

[www.pclinuxos.com](www.pclinuxos.com)

Good luck!

---

### Post by ThirdWorld on 2006-08-24
> **cmost said:**
> For excellent hardware detection and automatic compilation of video, wireless and other drivers via dkms please see PCLinuxOS.  A new version has recently been released; in three flavors depending on your needs:  MiniME (minimalistic), Junior (one best app for most common needs), and Big Daddy (full enchelada.)  You can get more details here:

[www.pclinuxos.com](www.pclinuxos.com)

Good luck!

looks really cool... thanks

---

### Post by ThirdWorld on 2006-08-24
what about opensuse? i tried freespire but i didnt like it. Looks unpolished.

---

### Post by tzulberti on 2006-08-24
Maybe you should tri Debian. Nevertheless, almost all distros doesn't use xfree86 since it is not free (as freedom), and they are using xorg instead. But Debian stable is still using xfree86.

---

### Post by ThirdWorld on 2006-08-24
thanks i will give it a try

---

### Post by ThirdWorld on 2006-08-24
well looks like debian dont have any live cds available. Thats bad. no way to try it without intall it.

---

### Post by msandersen on 2006-08-25
I tried Debian for the hell of it when 3.1 came out. It's not really a Desktop system. It's more designed as a stable Server system, hence the more conservative and relatively outdated package selection. They too will be moving to xorg in the next release, due by the end of the year. I don't know much about the difference between xfree86 and xorg, other than xorg is a recent fork and thus pretty much the same thing still (the recent version 7 is simply just a modularised version of xfree86). 
I am running Ubuntu on an old 500Mhz machine with a Rage 128 Pro card. Not exactly fast, but as well as can be expected of the hardware I guess. Wouldn't play games with it (it's the same on the Windows partition). It uses the standard "r128" driver. Works fine. 
Don't think PCLinuxOS will be any different in that regard. I think dkms (Dynamic Kernel Module Support) is only for the modern NVidia/ATI cards. It automatically compiles the display driver when upgrading the kernel. It would fall back to the default r128 driver for your card. As far as I know, they use xorg too. It's based off current Mandriva sources.
Coincidentally I'm writimg this from a PCLinuxOS live CD since I downloaded it yesterday. Of note is that since it is Mandriva-based, you have the Mandrake control center, it's KDE-based, but unlike Mandriva, it uses Synaptic for its package managemen using apt-rpm, sort of half-way between Mandriva and say Mepis or Kubuntu.
If I wanted KDE though, I think I'd prefer Mepis. I'm downloading the latest v6 right now, released in the past week. They used to use the Debian repositories until recently. They changed to using the Ubuntu repositories, since the Debian Unstable and even Testing branch has become unstable due to an increased pace of development, assumed by some to be due to the pressure from Ubuntu.
But because I prefer Gnome, and because I like the security of an organisation like Canonical behind it as opposed to a few part-time hackers, I use Ubuntu. SuSE is another option, but after my experiences with Mandrake, decided RPMs wasn't the way. Maybe Apt-RPM is better. PCLinuxOS aim to have it be able to auto-update the system the way apt-get can.

---

### Post by august_rzl on 2006-08-25
> **ThirdWorld said:**
> Please i need to choose another distro. in ubuntu my video card (Rage 128 Pro Ultra) doesnt work. No video aceleration and no way to play old games that are available in the repositories like hexen, quake 2 etc. I have asked many times how to install xfree86 but looks likes no one knows or probably the people who knows are not available. So guys which will be a good distro that could support xfree86? opensuse? freespire? fedora?

Thanks
Why do you want to go to another distro? Just use Ubuntu, search the driver, or go to [:) ]("http://help.ubuntu.com")

---

### Post by peabody on 2006-08-26
> **llamakc said:**
> Debian Potato.

I'm sure the humor in this was lost on a lot of people :).

---

