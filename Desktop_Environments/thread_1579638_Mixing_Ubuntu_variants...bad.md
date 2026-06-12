---
title: "Mixing Ubuntu variants...bad?"
date: 2010-09-22
forum: Desktop Environments
---

### Post by ClyN3il on 2010-09-22
I like to download and try anything and everything I can get hands on, and install anything from the repos that I think I might ever want to try or use...

Are there any problems that might occur when installing other Ubuntu versions on top of the previously installed flavour(s)? I mean for example, running apt-get kubuntu-desktop. And then xubuntu-desktop...and then edubuntu-desktop...and why stop there? Ubuntustudio-desktop, etc...

I've done this quite a few times. Predictably I've run into a few hiccups here and there, but for the most part it's been fine.

Once I even installed Mint Isadora, and then, after installing an Ubuntu desktop meta-package or two, upgraded to Maverick beta. Not surprisingly, there were some quirks, but it worked, and my computer didn't explode.

(This supports my contention that Mint is actually Ubuntu with a facelift--a very nice facelift that is worth getting!)

Here are a few quirks I've experienced:

[LIST]
[*]Default applications taking over, and having a hard time changing them back. Ie, Gnome places menu in particular sometimes will launch Dolphin or Thunar instead of Nautilus, even when Nautilus appears to be selected in all the places you would expect. (I found the solution but can't think of it off the top of my head...some obscure Gnome configuration setting.)
[*]Problems using wireless after the KDE network manager supplanted Gnome's. That was a while ago, and I haven't experienced that problem lately. However, even now with the very latest versions available, Gnome still seems much better at wireless signals (finding them, connecting, staying connected, etc.)
[*]Lots of programs crash when I start the occasional Xubuntu/XFCE session--usually I use the default/Gnome.
[*]Menus cluttered with redundant apps...although this isn't really a bug. More apps (and themes) is the main reason why install other variants. Currently, Gnome is my favourite, but KDE has some apps that are better than the Gnome equivalent--ie Kate and K3b, and some useful apps without an equivalent in Gnome, like Ktouch and Kitten. OTOH, it would be nice if there was a feature that allowed you to toggle between showing all apps in your menus, and filtering by which desktop they were meant for. (Maybe I'll make it someday.)
[*]When I converted/upgraded Mint Isadora to Ubuntu Maverick (I'm guessing this is not recommended), my system info screenlet told me that my OS was Debian-squeeze. Not a problem, but strange, and I have no idea why it would do that.
[/LIST]

I'm just wondering if this sort of thing is generally considered ok/safe. Does anyone know of any particular problems you would expect it to cause? Any precautions you should take or ways of doing it that would be less problematic?

---

### Post by nothingspecial on 2010-09-22
I`ve seen alot of people have problems.

If you just want to try a new desktop environment then I`d say just install the desktop environment, not the whole distribution
```

sudo apt-get install kde-minimal xfce4 lxde
```

etc etc

---

### Post by LinuxPhreak on 2010-09-23
> **nothingspecial said:**
> I`ve seen alot of people have problems.

If you just want to try a new desktop environment then I`d say just install the desktop environment, not the whole distribution
```

sudo apt-get install kde-minimal xfce4 lxde
```etc etc
 
I agree with the above poster. It will save you alot of HD space. And if all your concerned about is learning about other envirnments that is exactly what I would suggests.

I would also recomend trying VM's. I love VM's mostly because I'm a programmer, and I have more of an insurance that I wont screw up my main system when testing program. Worse comes to worse I screw up the VM. 

Names of VM's

[LIST=1]
[*] QEMU
[*]Virtual Box OSE (Virtual Box Open Source Edition, from what I hear it is built off of QEMU)
[*]VirtualBox (Propriatory version of VirtualBox, this is the only Propriotory Software I have installed on my computer. It is free of charge)
[*]VMWare (Never used it but here lots of stuff about it)
[/LIST]

---

