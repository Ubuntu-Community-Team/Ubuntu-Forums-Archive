---
title: "which distro should I use?"
date: 2008-07-30
forum: Debian
---

### Post by wildman4god on 2008-07-30
A friend has a compaq armada 1700 laptop, it has a 233 MHz pentium II, 94 Mb of ram and a six gig hard drive. It also has 1 usb port, two pcmcia slots, and a cdrom drive. My friend wants me to put linux on it so he can use the internet with a netgear wg511v2 wifi b/g card and he wants to rip music onto his creative zen xtra jukebox, which obviously requires gnomad2. I managed to put xubuntu on it but it runs slow, to slow for my taste, I was wondering if there was a better distro for it. It has to have automatic usb device mounting, and be debian based so i can install multi media codecs and gnomad2. I have already tried dsl and puppy linux but installing software is almost impossible since the have there own file type and when i tried them they would not rip cds or play any media like they were supposed to and they were not that user friendly and my friend isn't exactly the smartest thing to ever walk the earth, so should i stick with xubuntu or is there a better way of doing this?

---

### Post by tamoneya on 2008-07-30
xubuntu may work alright but I prefer Damn Small Linux

[http://www.damnsmalllinux.org/](http://www.damnsmalllinux.org/)

---

### Post by df6269 on 2008-07-30
You can chose LXDE Lightweight X11 Desktops Environment for xubuntu.

---

### Post by benuski on 2008-07-30
You could do a netinstall of Debian, untick the 'Desktop Environment' and 'Standard System' tabs, and then aptitude install xorg and fluxbox/openbox/icewm and rox-filer to be a file manager.  You would have a really light system that way.

If you want to go that way, I would recommend checking out the Debian forums, they have a lot of information about it there.

[http://forums.debian.net](http://forums.debian.net)

---

### Post by lukjad on 2008-07-30
Try Puppy Linux. My favourite variant is TEENpup. It's worth a shot. 

[www.puppylinux.org/](www.puppylinux.org/)

[http://www.puppylinux.org/wiki/archives/old-wikka-wikki/categoryderivative/teenpup](http://www.puppylinux.org/wiki/archives/old-wikka-wikki/categoryderivative/teenpup)

---

### Post by wildman4god on 2008-07-30
I can't do a net install being the wlan card requires the use of ndiswrapper to work and the computer has no ethernet and I tried puppy linux and dsl and while i did like them they didn't play media and installing new software is not that easy. I might check out teenpup but for now i am going to try lxde because i am a huge fan of ubuntu and its ease of use as well as it being easy to install new software using add/remove software. this comes in handy when getting stuff like codecs. thanks for the input.

---

### Post by lukjad on 2008-07-30
Hey, if you can, you *buntu it!

---

### Post by phoenix_abhi on 2008-07-30
> **wildman4god said:**
> A friend has a compaq armada 1700 laptop, it has a 233 MHz pentium II, 94 Mb of ram and a six gig hard drive. It also has 1 usb port, two pcmcia slots, and a cdrom drive. My friend wants me to put linux on it so he can use the internet with a netgear wg511v2 wifi b/g card and he wants to rip music onto his creative zen xtra jukebox, which obviously requires gnomad2. I managed to put xubuntu on it but it runs slow, to slow for my taste, I was wondering if there was a better distro for it. It has to have automatic usb device mounting, and be debian based so i can install multi media codecs and gnomad2. I have already tried dsl and puppy linux but installing software is almost impossible since the have there own file type and when i tried them they would not rip cds or play any media like they were supposed to and they were not that user friendly and my friend isn't exactly the smartest thing to ever walk the earth, so should i stick with xubuntu or is there a better way of doing this?

Go for this. [http://archlinux.org/]("http://archlinux.org/")

> Arch Linux is a general purpose Linux® distribution that can be molded to do just about anything. It is fast, lightweight, flexible, and most of the parts under the hood are quite simple to understand and tweak, which can make it a good distro to "learn the ropes" on. We do not provide any configuration helper utilities (ie, you won't find linuxconf in here) so you will quickly become very proficient at configuring your system from the shell commandline.

Arch Linux uses i686-optimized packages which gives us improved performance over some of our i386-optimized cousins. This means that Arch Linux will only run on a Pentium II processor or higher. We try to stay fairly bleeding edge, and typically have the latest stable versions of software 

---

### Post by basenvironment on 2008-07-31
debian...of course :D

In my opinion even xfce will be a bit heavy on that system, maybe if you do a light tight xfce install with thunar and thunar-volman to manage the removable drives and media. Heck, even gnome if you keep it **really** slim do not install heavy applications.

Personally I would go for a lighter desktop like icewm which is about as light as it gets for everything it provides. You would need to decide on a good file manager since one is not included. It would take more initial setup but the result would be better IMO.

---

### Post by snowpine on 2008-07-31
Check out Crunchbang; it is basically Ubuntu with Openbox. Very user-friendly and fast.

---

### Post by sujoy on 2008-08-01
slackware or debian with openbox/fluxbox/xmonad etc

---

### Post by tel93 on 2008-08-02
Xubuntu, Crunchbang, Fluxbuntu and any other Ubuntu-based OS (except for CLI) will DRAG! So will Puppy.

IMO use DeLi, or better yet, Debian or Arch (if your chip is i686).

---

### Post by mikjp on 2008-08-02
My summary of ten distros for lightweight installation: can be found [here](http://lightlinux.blogspot.com/2008/06/top-10-of-lightweight-linux_24.html).

In any case, you have to forget multimedia codecs. P233 is just not enough for multimedia (maybe mp3's would play?). Ripping might take forever. 

Try Slackware or Debian. Use IceWM, openBox, FluxBox, BlackBox as window manager. Or use the laptop as a X terminal for something build in this millenium :-)

Greetings,

mikko

---

