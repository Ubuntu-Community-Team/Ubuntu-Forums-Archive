---
title: "[SOLVED] Simple way of installing netbook remix"
date: 2008-10-09
forum: Desktop Environments
---

### Post by IanB2 on 2008-10-09
I have a clean copy of ubuntu running in a virtual machine and have tried to install netbook remix as I want to investigate this option for my Acer One.

I've downloaded and installed all the packages from launch pad and have the desktop sort of working. 

There must be an easy way of installing remix without having to download each package from the web site. I've been unable to find any instructions on how to do this. Any one know?

Also, I'm not sure I have a complete system as the when I switch to the remix desktop, the CPU usage seems to go to 100% and the machine slows right down and is very unresponsive. Any ideas what I'm doing wrong? (Everything is up to date as I've added the source listings to the system.)

---

### Post by cwsnyder on 2008-10-09
I do not have a netbook, but from what I have read, the netbook remix includes many changed drivers which expects the netbook environment.  For example, the kernel is stripped down for drivers to be expected on the netbook, reduced screen resolution, etc.  One modification which I have seen would change the processor speed!

This does not sound as if this is a good candidate for virtualization unless you have a virtual enviroment which includes emulation of the same hardware as the target netbook.

---

### Post by IanB2 on 2008-10-15
> **cwsnyder said:**
> I do not have a netbook, but from what I have read, the netbook remix includes many changed drivers which expects the netbook environment.  For example, the kernel is stripped down for drivers to be expected on the netbook, reduced screen resolution, etc.  One modification which I have seen would change the processor speed!

This does not sound as if this is a good candidate for virtualization unless you have a virtual enviroment which includes emulation of the same hardware as the target netbook.

Thanks for your comments .... makes sense.

---

### Post by Tux Aubrey on 2008-10-15
I started doing the same thing (trying to test the remix in a VM) for the same reason (Acer One) and have come to same conclusion (not a good idea).

I decided to wait until there is more clarity about how the remix will be delivered to non-OEM users.  LaRoza also posted a screen shot of the default desktop of his/her :) new Dell netbook here:

[http://img387.imageshack.us/my.php?image=screenshot3ok3.png](http://img387.imageshack.us/my.php?image=screenshot3ok3.png)

I thought that machine was coming with the Remix but that's not what I installed!

I know someone started to put an iso together for the Acer One - but seems to have crashed and burned.

I think the kernel now in Ibex is fully compatible (but not necessarily tuned) for the Atom cpu.  When that is a little more stable, I will try it on the One and see if I can get the remix working.

In the meantime, I'm very happy with Xubuntu 8.04.1with e17.  It is fast and stable and very pretty!

[My Current Acer One Desktop]("http://cafelinux.org/OptickleArt/displayimage.php?album=9&pos=28")

---

### Post by markbuntu on 2008-10-15
Here are directions for getting ubuntu and netbook remix on your Aspire One

[https://help.ubuntu.com/community/AspireOne](https://help.ubuntu.com/community/AspireOne)

---

