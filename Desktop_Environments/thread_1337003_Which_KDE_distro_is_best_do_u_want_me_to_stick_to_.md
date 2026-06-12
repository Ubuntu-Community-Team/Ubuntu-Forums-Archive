---
title: "Which KDE distro is best? do u want me to stick to GNOME ?"
date: 2009-11-25
forum: Desktop Environments
---

### Post by chinmaya_n on 2009-11-25
Hi

I need a suggestion .... 
Since one and half year i've been using UBUNTU(gnome).
But now i would like to change to a distro with KDE!
Which will you suggest for me?
I read that KUBUNTU is not that good as other KDE distros(i really dont know which are better than KUBUNTU;))

Or do you suggest me to stick to gnome!
Every suggestion is appreciated!:popcorn:

---

### Post by jacobs444 on 2009-11-25
stick to gnome, it is more stable than kde, but if you want kde and gnome, then search for kde in synaptic and install the kde packages. use the options on boot to change session to kde.

---

### Post by coffeecat on 2009-11-25
From what I've read either openSUSE or Mandriva are the best choices if you want to go with KDE and have user-friendliness. But if you go for one of them, you'll have not just a different desktop to learn, but a lot of different adminstrative tools, most importantly the package managers.

But with the release of the latest version of the 4.x series of KDE, I believe Kubuntu is now very good. So, I have a suggestion for you. You are running Jaunty, correct? Why not install 9.10/Karmic? Install the Ubuntu/gnome version. Do a fresh install, not a dist-upgrade. Once installed, apply all the updates to get it running smoothly, and then install the package 'kubuntu-desktop'. Be warned, this will be a hefty download of about 2-300MB. Once that is installed, you can choose either gnome or KDE from 'options' at the login screen.

Gnome and KDE will not interfere with each other and you can run KDE apps in gnome and vice versa. If you do that, you'll have the familiarity of gnome to go back to if you need to, the familiarity of *buntu, and the newest version of KDE to explore whenever you want.

---

### Post by Zorael on 2009-11-25
Whether we want you to use the one or the other doesn't matter. Do try it out and see if you like it, but beware; mixing GNOME and KDE *will* cause you issues. I'm not saying they're unresolvable, but you will need to deal with them. For an example, just search these forums for 'kde pulseaudio no sound'. You'll be able to switch back to GNOME if you don't like it though, so it's a good choice in that regard.

Just don't chalk it off to KDE being useless/unstable/whatnot, but to your system having an Ubuntu installation with KDE packages added to it, as opposed to being a Kubuntu installation. "GNOME is more stable than KDE" is a pretty broad claim, and one becoming increasingly contestable. Though I concede, GNOME is certainly more feature-stable. ;3

As for distros, I find that KDE is KDE. Kubuntu is a pretty plain KDE distro, with no extra art or anything to brand it Kubuntu except the usplash and the little logo on the menu. OpenSUSE has its own refactoring of the Air theme with another color, wheras Kubuntu uses the standard Air. I'll admit I haven't tried Mandriva yet, though.

---

### Post by RodGer GR on 2009-11-25
I have installed Karmic Koala but I also have Hardy Heron and as so I still use the old grub version (on a dedicated partition) with the menu.lst. I've learned good enough how to edit the menu.lst file.
I would be grateful if somebody could tell me what would happen if I downloaded kde-desktop for my 9.10 installation. Would it create a new kernel which I can add to my menu.lst or it is something more complicated than this?
Thanks in advance.

---

### Post by coffeecat on 2009-11-25
> **RodGer GR said:**
> I would be grateful if somebody could tell me what would happen if I downloaded kde-desktop for my 9.10 installation. Would it create a new kernel which I can add to my menu.lst or it is something more complicated than this?
Thanks in advance.

Don't worry, it won't affect grub at all. If you install kubuntu-desktop in a pre-existing intallation of Ubuntu/gnome, it will share the same kernel, most of the rest of the OS and the xserver. It's really only the desktop environment that is different. 

Once you've installed kubuntu-desktop, you choose the same Karmic entry in your grub menu, but once you get to the login screen you can choose either gnome or KDE under 'options'. With earlier releases of Ubuntu, if you installed kubuntu-desktop in Ubuntu, kubuntu would hijack the usplash and replace the gdm login screen with the kdm one. Which meant that you got a blue boot sequence rather than a brown one. Which some people might think is no bad thing. :wink: But I don't know whether this is true of Karmic and xsplash. Whatever - only the appearance changes, not the functionality.

By the way - the package you want is kubuntu-desktop, not kde-desktop. There is a 'kde-full' package in the repositories which I believe gives you vanilla KDE, but as the Kubuntu version of KDE is little changed from vanilla KDE anyway, you might be better off with kubuntu-desktop.

---

### Post by chinmaya_n on 2009-11-25
> **RodGer GR said:**
> 
I would be grateful if somebody could tell me what would happen if I downloaded kde-desktop for my 9.10 installation. Would it create a new kernel which I can add to my menu.lst or it is something more complicated than this?

You dont get a new entry in menu.lst!
You will get a new entry in the sessions list while you login your system...
After installing kubuntu-desktop for ubuntu, you will see a new entry in the sessions during login (username & passwd etc.,). Select KDE there to enter KDE or Gnome to Gnome!
You can keep anything default!

---

### Post by chinmaya_n on 2009-11-25
> **Zorael said:**
> Whether we want you to use the one or the other doesn't matter. Do try it out and see if you like it, but beware; mixing GNOME and KDE *will* cause you issues. I'm not saying they're unresolvable, but you will need to deal with them. For an example, just search these forums for 'kde pulseaudio no sound'. You'll be able to switch back to GNOME if you don't like it though, so it's a good choice in that regard.


I tried by installing kubuntu desktop before... but removed it!
B'se i found it slow ! Did i felt that or Is it real? (I dont know!)
I found GNome running behind KDE! (While shutting down the system i could see the Gnome desktop suddenly and disappears) Even this happens at sometimes while i start some applications! :?:
I dont know to what extent my observations are correct!
What will you say?

---

