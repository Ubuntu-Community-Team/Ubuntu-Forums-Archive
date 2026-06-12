---
title: "Two kernels plus two desktops"
date: 2008-12-27
forum: General Help
---

### Post by TheMyself on 2008-12-27
I think there are some redundancies in my Ubuntu installation. Firstly when I start the computer, I have two choices of Linux kernel:

Ubuntu 8.10, Kernel 2.6.27-9-9-generic

Ubuntu 8.10, Kernel 2.6.24-19-9-generic  

I've never used the second one. When I first installed Ubuntu there was only one kernel.


Secondly, my original installation was with the default GNOME desktop and then I installed complete KDE desktop as well but my default is GNOME. When I boot the computer the "KUBUNTU" logo  is first displayed and then GNOME login window kicks in. This doesn't sound right to me. I use KDE only occasionally (also use some KDE applications in GNOME) so starting the computer with Kubuntu does not sound great. Can I fix this without uninstalling KDE?

---

### Post by jerome1232 on 2008-12-27
> **TheMyself said:**
> I think there are some redundancies in my Ubuntu installation. Firstly when I start the computer, I have two choices of Linux kernel:

Ubuntu 8.10, Kernel 2.6.27-9-9-generic

Ubuntu 8.10, Kernel 2.6.24-19-9-generic  

I've never used the second one. When I first installed Ubuntu there was only one kernel.

As you update your system you will get new kernels, the old one don't get automatically deleted, I always keep at least 1 or 2 old ones around, just in case a new updated kernel comes along and breaks my system past booting (then you just pick the old kernel and everything works again)

If you eve decide to delete old kernels you do this (let's say you wanted to get rid of 2.6.24-19-9-generic)
```
sudo apt-get remove linux-image-2.6.24-19-9-generic
```

> **TheMyself said:**
> 
Secondly, my original installation was with the default GNOME desktop and then I installed complete KDE desktop as well but my default is GNOME. When I boot the computer the "KUBUNTU" logo  is first displayed and then GNOME login window kicks in. This doesn't sound right to me. I use KDE only occasionally (also use some KDE applications in GNOME) so starting the computer with Kubuntu does not sound great. Can I fix this without uninstalling KDE?

That's because when you install kubuntu-desktop it install's kubuntu usplash image and configs it as the default, if you want it back to the regular Ubuntu the easiest way is with startup manager

```
sudo apt-get install startupmanager
```
System->Administration->Startup Manager select the usplash image you would like to use in here. (I don't have it installed right now so I can't see where the exact option is, but you should be able to figure it out)

---

### Post by TheMyself on 2008-12-27
So, i's just the image and the same thing goes on in the background. Thanks for the information.

---

