---
title: "What needs to be installed to make mac/window software to work?"
date: 2009-03-14
forum: General Help
---

### Post by italiaskippy on 2009-03-14
I just got my new Dell Mini and love it. It came with Ubuntu and works great. I have an external CD ROM drive (no problem there) and I downloaded codeweavers (for dummies) so I could run my school cds (questions and answers). I can see the setup.exe file but it won't open. 

I know that I have to install some type of software in order to make it work. I don't wish to download everything i.e. an entire windows OS. 

It will also run on mac. Codeweavers has a download to integrate between the 2 platforms and I would prefer to go that route. 

Can someone please tell me how to do this in a simple way or another solution to the problem? I am in RN school and really need this badly...

Much obliged:D

---

### Post by mb_webguy on 2009-03-14
Wine will allow you to run some (but not all) Windows software on Linux.  Follow [these instructions]("http://www.winehq.org/download/deb") to install Wine.  After that, you should be able to run (some) Windows software as you would normally.

Currently, there's no way to run Mac software on Linux, though there are several such projects in development.

---

### Post by lovinglinux on 2009-03-14
To install Windows applications you need Wine to "emulate a Windows environment".

To install Wine run this command in the console:

```
sudo apt-get install wine
```

Then you can double-click in the setup.exe to install it.

Not all applications will work under wine. Check if the application you need works fine at [http://www.winehq.org/](http://www.winehq.org/)

---

### Post by D.Gelman on 2009-03-14
I am someone who moved to Ubuntu from Windows. I often find the need to run Windows applications in order to remain compatible with the mainstream computing world, and in order to satisfy this I use two methods: running commonly used applications with Wine; using VirtualBox (free from Sun Microsystems) to run a Windows XP installation for applications that are not compatible with Wine.

Wine is the better option, but will not work for everything. This website lists many Windows applications and details about how they work in Wine: 
[http://appdb.winehq.org/](http://appdb.winehq.org/)

VirtualBox is available from Sun Microsystems here:
[http://www.virtualbox.org/](http://www.virtualbox.org/)

---

