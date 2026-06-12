---
title: "installing xfce, gnome and kde into GRUB selection"
date: 2011-12-05
forum: Desktop Environments
---

### Post by markMDW on 2011-12-05
Is it practical and reliable to install two or three desktop environments on a single 'ubuntu system?  I've used gnome and xfce and like some of the features of both.  I'd also like to test out KDE.  But, I really don't want to setup a GRUB boot loader to select between the them.  Besides, I still haven't figured out why GRUB says "Ubuntu" and gives numerous seemingly identical choices on the systems that have a Windows option in the bootup.

It would be fantastic to be able to select between Kubuntu, Xubunt, Ubuntu or XFCE, KDE, Gnome and still retain the same HOME FOLDER and USER NAME / LOGIN no matter which I choose.
Can I just install the XFCE or Gnome or KDE Desktop from Ubuntu Software Center and then expect to have the choice on login after selecting "Ubuntu" from GRUB or will my migrate my Ubuntu system into the last Desktop Environment ..permanently?  A while back I've read that it can be setup as a choice but I don't see that information now.  I've also read somewhere else that it can be done but is unreliable.  I want to use GNOME sometimes and XFCE other times, and would like to try out KDE occasionally.  Thanks for everyones suggestions!

---

### Post by IWantFroyo on 2011-12-05
The entries in GRUB that seem almost identical to Ubuntu are probably old kernels and a memory test/recovery mode. When a new kernel update is downloaded, you get a new entry in GRUB.

You can install other desktops from the Software Center, and then select them while logging in. All your data will still be there, and you don't need to even touch GRUB.
You can also install desktops like this:
```
sudo apt-get install kubuntu-desktop
```
(That's KDE; XFCE is xubuntu-desktop, and Gnome Shell is gnome-shell).

The login manager will remember your choice after a login or two, and will let you keep choosing whatever environment you want.

Installing multiple desktops is practical as long as you have enough space. If that's no trouble, then there's nothing wrong with it.

---

### Post by markMDW on 2011-12-05
Thanks very much for the excellent information!  I'm going to do just that.
:popcorn:

---

### Post by IWantFroyo on 2011-12-05
Glad to help!

I would also encourage looking at some WMs like scrotwm and Openbox. Check out some screenshots of CrunchBang to see what Openbox looks like set up.

---

### Post by markMDW on 2011-12-05
Wow, Thanks again!  

I'm checking out CrunchBang/OpenBox, sounds like its highly customizable.  This might be just what I'm looking for.  I'd like to one day learn how to create my own unique special use distribution and create an ISO of it for myself and a few others.  There are some utilities that allow you record an ISO of a setup, I've heard.  

scrotwm tiling system looks like it could be used for a computer kiosk.  it might actually turn out to be more of what I'm looking for to experiment with (once I learn more about it).  
:KS

---

