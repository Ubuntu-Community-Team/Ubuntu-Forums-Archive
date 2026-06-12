---
title: "setting up multiple desktop managers"
date: 2008-01-19
forum: Desktop Environments
---

### Post by jmbenson89 on 2008-01-19
I have seen linux machines setup where when you login in, you can choose a session/desktop manager.  I was wondering how I could setup Ubuntu 7.10 with multiple desktop managers.  Specifically, Gnome, KDE 4.0, XFCE, Fluxbox and maybe a few more (what else can I try out?).

Thanks ahead of time!

---

### Post by oldos2er on 2008-01-19
You install them through Synaptic (that's the easiest way). When you logout, then log back in, you should see the choices under the 'Session' menu.

---

### Post by jmbenson89 on 2008-01-19
Ok I will try that.  Is there also a way to load up multiple WM/DE at the same time and switch between them quickly?  If so, would each WM/DE manage the programs separately, or (for example) if I have Firefox open in one, would it also be open in the other?

---

### Post by Thund3rstruck on 2008-01-19
> **oldos2er said:**
> You install them through Synaptic (that's the easiest way). When you logout, then log back in, you should see the choices under the 'Session' menu.

I wonder if any performance hit is incurred by having all the libraries and packages installed on the machine to support 3-4 separate window managers?

---

### Post by glotz on 2008-01-19
[QUOTE=jmbenson89](what else can I try out?)[/QUOTE]See [http://xwinman.org/](http://xwinman.org/)

[QUOTE=Thund3rstruck]I wonder if any performance hit is incurred by having all the libraries and packages installed on the machine to support 3-4 separate window managers?[/QUOTE]There should be no performance hits. That stuff will just sit on the disk. However, there can be some strange interactions, bugs, for example I use Ubuntu as in GNOME and decided to give Xfce a try. Both use the same (Debian?) menu and now my GNOME menu is noticeably slower...

---

### Post by oldos2er on 2008-01-19
I suppose you could create a virtual machine and run each DE in it. Other than that, I don't think there's a way to run them simultaneously; they'd probably cause lots of graphical problems.

 If you're just wanting to run a KDE program on Gnome, or vice versa, you just go through the usual program installation process with apt-get or Synaptic. No need to install more than one DE.

"I wonder if any performance hit is incurred by having all the libraries and packages installed on the machine to support 3-4 separate window managers?"
 It'll take a fair amount of hard disk space. But since you can only run one DE at once, I don't see a real performance hit.

---

### Post by adityam on 2008-01-20
> **jmbenson89 said:**
> Ok I will try that.  Is there also a way to load up multiple WM/DE at the same time and switch between them quickly?  If so, would each WM/DE manage the programs separately, or (for example) if I have Firefox open in one, would it also be open in the other?

See the thread

[http://ubuntuforums.org/showthread.php?t=271674](http://ubuntuforums.org/showthread.php?t=271674)

---

### Post by urukrama on 2008-01-20
> **jmbenson89 said:**
> (what else can I try out?).

If you like light environments, try Openbox, Pekwm, or Icewm. For the first two, check the links in my signature, for Icewm see [here]("http://psychocats.net/ubuntu/icewm").

They don't take much space on your hard disk. Even KDE, Gnome and Xfce don't really take *that* much, provided you install the kde-core, gnome-core and xfce4 packages instead of the kubuntu-desktop, ubuntu-desktop and xubuntu-desktop. You won't get all the extra apps that come with the latter metapackages, but you will have a functional (and faster) desktop environment, to which you can add whatever else you need.

---

