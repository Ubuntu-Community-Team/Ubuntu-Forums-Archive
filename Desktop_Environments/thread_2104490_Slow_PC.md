---
title: "Slow PC"
date: 2013-01-13
forum: Desktop Environments
---

### Post by jb2012 on 2013-01-13
Hi, I'm new to the Ubuntu OS and have installed the latest Ubuntu onto an old PC. Ubuntu loads OK however using the included programs and the Ubuntu programs are painfully slow in opening and closing.

The specification of the PC is as follows.

Ascer Aspire T-135-S870
AMD Semperon 64 3000 + FSB 800 Mz
80Gb HDD
DDR Ram 2Mb

I would like to know why I have this problem please and how to resolve the problem.

---

### Post by sudodus on 2013-01-13
Welcome to the Ubuntu Forums :-)

The new standard (or 'vanilla') Ubuntu is made for rather new and powerful computers. The desktop environment Unity has a lot of eye-candy, but needs a lot of CPU horsepower and also RAM and a good graphics card. By the way, what graphics card/chip is there in the computer?

But there are good alternatives in the Ubuntu family.

***Xubuntu*** has the light-weight desktop environment XFCE, and will probably run very well on your computer.

***Lubuntu*** has the ultra light-weight desktop environment LXDE, and will run even faster on your computer, but of course, there is less eye-candy.

Download the iso files and try these flavours of Ubuntu live before deciding what to install.

---

### Post by cmcanulty on 2013-01-13
or install ubuntu and then install gnome-panel and get the classic interface works for me with GB ram
[http://www.omgubuntu.co.uk/2012/03/gnome-classic-in-ubuntu-12-04-its-like-nothing-ever-changed]("http://www.omgubuntu.co.uk/2012/03/gnome-classic-in-ubuntu-12-04-its-like-nothing-ever-changed")

---

### Post by Cheesemill on 2013-01-13
How much RAM does that machine have?

---

### Post by cmcanulty on 2013-01-13
sorry I meant to type 1GB ram and it runs fine in Ubuntu classic, no effects 12.04 2GB would be a lot faster and set up 2-4 GB of swap

---

### Post by jb2012 on 2013-01-14
> **Cheesemill said:**
> How much RAM does that machine have?

2Gb as stated in my first post.

---

### Post by deadflowr on 2013-01-14
Yeah, Ubuntu can be slower on older machines.
But look at it this way, the speed it's running at now freshly installed is relative and comparable to the speed it will be running in six months, ten months, or two years. But that also depends on how much tweaking you might do in the interrum. 

I would agree though that a lighter distro such lubuntu or xubuntu might give you an added boost. they are both quite good, and share alot with Ubuntu.

---

### Post by deadflowr on 2013-01-14
> **jb2012 said:**
> 2Gb as stated in my first post.


The first post says 2MB, not GB. So the confusion on the listing of such little RAM is certainly understandable.

---

### Post by claracc on 2013-01-14
I recommend lubuntu 12.04, it works smoothly in old hardware, using little resources.

As you have 2 GB RAM, lubuntu has to fly in the machine.

---

### Post by mysteriousdarren on 2013-01-23
Use 12.04 Lubuntu and install the latest AMD drivers. If your worried about being slow, uninstall slower programs and replace with lighter replacements. I always do, and makes a world of difference. I'm writing this on my netbook running Lubuntu 12.04 and it flies.

---

### Post by Warren Hill on 2013-01-23
The Unity desktop is slow compared to that used in earlier versions of Ubuntu.

You can try Gnome Classic 
```
sudo apt-get install -y gnome-session-fallback
```
log out then back in selecting "Gnome Classic (No Effects)" as your desktop.
Click the circular icon next to your user name and the password entry box to change your desktop.

If that is still not fast enough take a look at xubuntu or lubuntu.  These are lighter and faster than Ubuntu but you still have access to all the same programs if you want.  The default install uses lighter weight apps but if you decide you want any of the apps from Ubuntu they are all in the software centre to install

---

