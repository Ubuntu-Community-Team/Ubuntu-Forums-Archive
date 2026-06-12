---
title: "X or Gnome"
date: 2007-08-19
forum: Desktop Environments
---

### Post by Geffers on 2007-08-19
I understand xubuntu to be suited to older machines.

Is there any advantage to installing xubuntu to a separate partition or is that just the same as installing Xfce Desktop and merely selecting that option at startup.

Geffers

---

### Post by Ozeuss on 2007-08-19
just to correct something- xfce is not the same as X. X is th windowing system that serve all DE's - gnome, KDE, and Xfce.
I think that it an only-xfce desktop wil be faster than a gnome-and-xfce, merely because you won't have to load the gnome libraries.

---

### Post by kellemes on 2007-08-20
> **Geffers said:**
> I understand xubuntu to be suited to older machines.

Is there any advantage to installing xubuntu to a separate partition or is that just the same as installing Xfce Desktop and merely selecting that option at startup.

Geffers

There will be not much difference indeed. Performancewise probably nothing..

---

### Post by kerry_s on 2007-08-20
Hmm, sounds like your looking for speed.
[http://www.psychocats.net/ubuntu/minimal](http://www.psychocats.net/ubuntu/minimal)

debian base + a wm = wow, that's fast :)

---

### Post by julian67 on 2007-08-20
If you install Xfce (xubuntu-desktop) on top of regular Ubuntu it might not be any quicker because your desktop will still be managed by Nautilus and your Window Manager will still be Metacity. You can change both of these of course but out of the box you won't be getting the real benefit of Xfce and if you change windows manager and desktop manager you might lose some features of Gnome that are handled by Metacity and Nautilus. 

Xfce/Xubuntu is not just for older computers. My Lenovo Y400 laptop is a 2007 model, it has Centrino Duo CPU and 1.5 GB RAM, SATA drive and so on.....hardly antique.... and it is very very fast using Xubuntu. Running Gnome or KDE was pretty frustrating whichever distro I tried.  I do run some Gnome apps such as Epiphany browser and Gnome Keyring Manager but I don't install anything that requires Metacity or Nautilus as I've noticed huge slow downs with these.  I also no longer run any KDE apps or libraries. For me Xfce is the right balance between the really minimal fast DE like fluxbox and the heavyweights like KDE and Gnome. It is massively faster than Gnome and KDE and hardly any different from fluxbox (tried as Mepis Antix and fluxbuntu among others). 

I think some of this is hardware dependent. I installed regular Ubuntu on a friend's desktop PC with a low end AMD 64 CPU and it is extremely responsive with all the Nautilus features enables and Beagle search and Deskbar and so on.  But on my laptops and another desktop I installed a few weeks ago (Athlon 2700, Radeon 900 pro, 1 GB RAM) Gnome is sloooooooooow but Xfce is super fast. I think I would usually install Ubuntu first and see how it goes because Gnome and Nautilus have so many great features and is friendly and easy for a new user.

btw Epiphany (the Gnome browser) starts up much, much quicker under Xfce than under Gnome :lolflag: Same goes for most Gnome apps.

---

### Post by julian67 on 2007-08-20
> **kerry_s said:**
> Hmm, sounds like your looking for speed.
[http://www.psychocats.net/ubuntu/minimal](http://www.psychocats.net/ubuntu/minimal)

debian base + a wm = wow, that's fast :)

I'm not sure that guide is any good. It prompts the user to install a server base system which is not a great idea if actually you want a minimal *desktop*. Much better to choose the option "Install a command-line system" and build on that. If you choose a server install you get a kernel optimised for server use. Servers and desktops typically have to deal with different loads so the kernels are different.

---

### Post by kerry_s on 2007-08-20
> **julian67 said:**
> I'm not sure that guide is any good. It prompts the user to install a server base system which is not a great idea if actually you want a minimal *desktop*. Much better to choose the option "Install a command-line system" and build on that. If you choose a server install you get a kernel optimised for server use. Servers and desktops typically have to deal with different loads so the kernels are different.

Nope! your so wrong. typing server just activates the base installer, it actually has nothing to do with a server. It all depends on what you use to install, the alternate you choose "Install a command-line system" , now if you use a mini.iso(aka:netinstaller) there is no "Install a command-line system", so you would type "server" to only install the base system, there is nothing server about, no special kernel, no server applications, nothing.

try reading the instructions before you jump to conclusions.

---

### Post by julian67 on 2007-08-20
> **kerry_s said:**
> Nope! your so wrong. typing server just activates the base installer, it actually has nothing to do with a server. It all depends on what you use to install, the alternate you choose "Install a command-line system" , now if you use a mini.iso(aka:netinstaller) there is no "Install a command-line system", so you would type "server" to only install the base system, there is nothing server about, no special kernel, no server applications, nothing.

try reading the instructions before you jump to conclusions.

By default Ubuntu server has a different kernel to Ubuntu desktop. You can see for yourself.

For example you can use synaptic to list the different kernels (linux-image-*) and you'll see the server kernel is different. The desktop kernel (i.e. linux-image-2.6.20-15-generic) is > Geared toward desktop systems and the server kernel (i.e. linux-image-server) is > for Server Equipment You can also see that even the kernel version numbers are different. 

also see [https://help.ubuntu.com/community/ServerFaq]("https://help.ubuntu.com/community/ServerFaq")

> Ubuntu server install by default a server optimized kernel

Perhaps the easiest and least confusing way to install a base desktop system is to use the regular alternate install CD and choose to install command-line system.

---

### Post by kerry_s on 2007-08-20
that's in the repo, that is not what gets installed by using "server" the only way your going to get that is by using the server edition installer or installing it yourself. 
if you've never done it, why would you say that is what it does? :mad:

done

---

### Post by julian67 on 2007-08-20
If the install option is "server" it should install the server kernel. That's what it did last time I installed ubuntu server using a regular 7.04 server CD. If the install option is "server" and it installs something other than the server kernel then it's not an installer that I'd use or recommend. If there is only a desktop kernel on the CD then the installer should not be showing a server option.

---

### Post by kerry_s on 2007-08-20
> **julian67 said:**
> If the install option is "server" it should install the server kernel. That's what it did last time I installed ubuntu server using a regular 7.04 server CD. If the install option is "server" and it installs something other than the server kernel then it's not an installer that I'd use or recommend. If there is only a desktop kernel on the CD then the installer should not be showing a server option.

that's a different cd, has nothing to do with the how to. you use the how to you get the right cd. there's nothing wrong with the how to if you follow it.
the server cd is for the server, what did you expect it to do?

---

### Post by julian67 on 2007-08-20
well however many times I read the howto you linked to it still advises, for a barebones install with the aim of running a IceWM desktop, to use the mini iso and "At the Boot: prompt, type "server"".  It's right there in plain English. If that method is good for you then fine, it's nice that you're happy with it.

---

### Post by kerry_s on 2007-08-20
> **julian67 said:**
> well however many times I read the howto you linked to it still advises, for a barebones install with the aim of running a IceWM desktop, to use the mini iso and "At the Boot: prompt, type "server"".  It's right there in plain English. If that method is good for you then fine, it's nice that you're happy with it.

exactly, the mini.iso is for the ubuntu-desktop, typing "server" activates another option for just the base system, but does not install nothing server related. your taking the meanig of "server" to mean it has to be a server with all the server stuff, it does not mean that when using the mini.iso.

---

### Post by julian67 on 2007-08-20
> **kerry_s said:**
> exactly, the mini.iso is for the ubuntu-desktop, typing "server" activates another option for just the base system, but does not install nothing server related. your taking the meanig of "server" to mean it has to be a server with all the server stuff, it does not mean that when using the mini.iso.

Yes in my bizarre interpretation of the English language the word server conveys the idea that this is somewhat related to server type things and may even be referring to......a server! Now I'm not sure if I'm running Ubuntu Desker or Ubuntu Servtop.......

---

### Post by kerry_s on 2007-08-20
> **julian67 said:**
> Yes in my bizarre interpretation of the English language the word server conveys the idea that this is somewhat related to server type things and may even be referring to......a server! Now I'm not sure if I'm running Ubuntu Desker or Ubuntu Servtop.......

LOL. "Hi, my name is kerry, i will be your server for this evening."
hey what do you know it can mean other things. :lolflag:

---

