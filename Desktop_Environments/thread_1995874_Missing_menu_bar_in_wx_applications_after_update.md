---
title: "Missing menu bar in wx applications after update"
date: 2012-06-03
forum: Desktop Environments
---

### Post by Michele S on 2012-06-03
OS: Ubuntu 12.04 LTS

After updating the OS with apt-get dist-upgrade I discovered that menu bar in wx applications are disappeared.

While in Unity there are no trouble, in Gnome-Shell and Gnome-Classic sessions the menu bars don't appears anymore.

I noticed the bug in these applications:

- Audacity
- wxMaxima

The package that has been updated are:

- libwxbase2.8-0
- libwxgtk2.8-0
- unity-lens-video
- software-center

---

### Post by [woodstock] on 2012-06-04
Hi all,

I can confirm that behavior. However, for me it does not work neither with Gnome 3 nor with Unity. I had hoped that logging in using Unity would fix the problem.

That's a pity since it seems that all wx applications are affected and we have some data analysis tool in our lab that rely an python-taits and python-traitsui and the wx interface. :-(

---

### Post by Wrapperband-0 on 2012-06-27
I've got this problem in Kubuntu with XFCE desktop. 

Audacity starts with no menu.
I can get the menu back in Audacity by pressing Ctr-N , which then starts a new instance with the menu back.

---

### Post by nairboon on 2012-07-10
A temporary workaround is switching the gnome theme and the menubar apears again.

[https://bugs.launchpad.net/ubuntu/+source/wxwidgets2.8/+bug/662077](https://bugs.launchpad.net/ubuntu/+source/wxwidgets2.8/+bug/662077)

---

### Post by RavanH on 2012-08-04
This bug sucks about as it seems to bring the horrors of Unity to the Gnome Shell. (= personal opinion, not meant to start a flame against Unity)

> **nairboon said:**
> A temporary workaround is switching the gnome theme and the menubar apears again.

[https://bugs.launchpad.net/ubuntu/+source/wxwidgets2.8/+bug/662077](https://bugs.launchpad.net/ubuntu/+source/wxwidgets2.8/+bug/662077)

Excellent! That works for poEdit, pySVN ( SVN Workbench) and rapidSVN too... Sadly, you have to do this EACH time you open the application :( but then again, it's a work-around. Thanks for sharing :)

---

### Post by MoonCactus on 2012-12-07
Cool, on kubuntu, I "simply" got rid of the bug with:

```
sudo apt-get remove appmenu-gtk
```

There were no package dependent on this one, so it was really smooth.

---

