---
title: "net install"
date: 2011-09-02
forum: Desktop Environments
---

### Post by Treken on 2011-09-02
was wondering if anyone could give me some suggestions as to building my own os from ground up? I know that certain apps require dependencies, and I need to have a minimal install. For instance, I need to have a browser, file manager, archiver, gimp-like program, terminal emulator, maybe wbar, login manager, and gedit-like program. is there a good way to select what I need that basically shares dependencies between one another so I don't have to download a bunch of extra dependencies for single apps? I hope I made it clear as to what I'm wanting to do and do hope I posted in the proper section of the forum.

---

### Post by hhh on 2011-09-02
[https://help.ubuntu.com/community/Installation/MinimalCD](https://help.ubuntu.com/community/Installation/MinimalCD)

If you are installing Gnome, KDE, Xfce or even LXDE an appropriate file manager, text editor and more will get installed as well. If you are building a stand-alone window manager setup, you will just have to make your choices and see what happens. Dependencies aren't a problem unless you are very seriously restricted by hard drive space, and some appications can be greatly slimmed down by installing via apt-get with the --no-install-recommends command. So, after installing the base system, some examples and using Ubuntu Natty sources...

Install Gnome...```
sudo apt-get install gnome
```
Install Gnome as it is on Ubuntu... ```
sudo apt-get install ubuntu-desktop
```
Install KDE...```
sudo apt-get install kde-full
```
... or...```
sudo apt-get install kubuntu-desktop
```

---

### Post by Treken on 2011-09-02
What I really needed was a tinycore with apt-get on it. I'm building a distro that has all the tools needed for android development that will fit on a cd. The tools alone are several hundred mbs

---

