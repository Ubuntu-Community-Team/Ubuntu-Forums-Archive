---
title: "Xfce 4.4.0 Problem!"
date: 2007-02-20
forum: Desktop Environments
---

### Post by cmulax on 2007-02-20
I just installed xfce 4.4.0 on a clean ubuntu install, using this howto:

[http://tech.tolero.org/blog/en/linux/xfce-440-packages-for-ubuntu-edgy](http://tech.tolero.org/blog/en/linux/xfce-440-packages-for-ubuntu-edgy)

However, whenever I go to Applications > Settings, certain options here do not work.  They are:

calendar settings, desktop settings, keyboard settings, mixer settings, mouse settings, sessions and startup settings, splash screen settings, user interface settings, window manager settings, window manager tweaks, and workspace settings

whenever I click on one of these, I get an error saying "Xfce Settings Manager error: No such plugin "workspaces"" or whatever plugin it happens to be.

I have looked through synaptic and such and it does not look like I am missing any plugins for 4.4.0, and I will continue looking, but if anyone has seen a similar problem or has a possible solution I would appreciate it very much!

---

### Post by kerry_s on 2007-02-20
Do you mean a clean Xubuntu install? What version dapper,edgy,feisty?
That repo is meant to upgrade edgy Xubuntu not install on top of gnome. You can try installing xubuntu-desktop to see if it will fix things.

---

### Post by cmulax on 2007-02-20
ah I apologize for lack of more specifics.  it is a clean ubuntu 6.10 edgy install with gnome, which i then installed xfce 4.4.0 from the repos.  When I do apt-get install xubuntu-desktop  it just says it is already the newest version.

I will probably try reinstalling ubuntu, then xubuntu-desktop then 4.4 to see if that works, but before I do would there possibly be a faster solution?

---

### Post by kerry_s on 2007-02-20
Why not just go straight for a xubuntu install? Here's the mini.iso, with this you can select which desktop you want among other things and it gets the latest as it installs so you will be mostly up to date.-> [http://archive.ubuntu.com/ubuntu/dists/edgy/main/installer-i386/current/images/netboot/mini.iso](http://archive.ubuntu.com/ubuntu/dists/edgy/main/installer-i386/current/images/netboot/mini.iso)

---

### Post by Rommidze on 2007-02-20
> **cmulax said:**
> ah I apologize for lack of more specifics.  it is a clean ubuntu 6.10 edgy install with gnome, which i then installed xfce 4.4.0 from the repos.  When I do apt-get install xubuntu-desktop  it just says it is already the newest version.

That is OK. I have installed XFCE 4.4 quite the same way.

> **cmulax said:**
> I will probably try reinstalling ubuntu, then xubuntu-desktop then 4.4 to see if that works, but before I do would there possibly be a faster solution?

Do not panic. Will fix it without reinstallation. At first of all you have to reinstall the settings panel and it's plugins packages. Execute this at the console:

```
sudo aptitude reinstall xfce4-mcs-manager xfce4-mcs-plugins
```

__________________________________
How to [protect blog or a forum from spam]("http://tech.tolero.org/blog/en/web/blogs-and-forums-spam-bots-protection").

---

