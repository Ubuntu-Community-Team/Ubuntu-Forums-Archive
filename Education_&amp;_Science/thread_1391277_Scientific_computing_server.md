---
title: "Scientific computing server"
date: 2010-01-26
forum: Education &amp; Science
---

### Post by lachose on 2010-01-26
Hi fellow ubuntuer!

I want to set up a server to do scientific computing in my lab. We do econometrics/statistics and have an occasional but not continuous need for more cpu than a good desktop pc can offer. Users will need a wide array of progs and compiler, most but not all of them available under linux. They should thus be able to run windoz sessions or progs. I'd like to make a ubuntu server as it is the distro I am most familiar with. 

Any leads I could start with for the choice of the distro and the hardware? Thanks in advance for your help.

---

### Post by stim on 2010-01-26
If you are looking for something high performance a standard ubuntu install will do just fine on a relatively fast box.  You should have a seperate box for windoze crap though, because it will

1) bog down the ubuntu box
2)defeat the purpose of running ubuntu on the box

---

### Post by gunksta on 2010-01-27
Distro - Ubuntu

Fact is, ANY strong Linux Distro should be able to meet your needs. Red Hat, Suse, Ubuntu, etc. But, Ubuntu has two advantages over other distributions. First it has a HUGE repository. Secondly, there are lots of external software resources. For example, many R users prefer to use the official R-CRAN repo because it is more up to date that what can be found in the default Ubuntu repository. And, many up-and-coming programs make Ubuntu packages available BEFORE binaries are available for smaller distros.

Regarding Windows - don't go Dual Boot. It's a waste of time. Buy a system with LOTS of RAM. I'm thinking in the 8-16 Gigs range. Get a AMD processor with 3 processors or an Intel/AMD with 4 cores. It will cost you a little more but you can then use Virtualbox, KVM, etc. to run a virtual Windows computer, making these applications available to users when necessary.

Good Luck

---

### Post by lachose on 2010-01-27
Thanks for the quick reply guys. I guess I'll go with gunksta's solution. Just wanted to make sure that ubuntu can support properly a machine with 8 16 or whatever number of cores

---

### Post by gunksta on 2010-01-27
Perhaps I was confusing (or confused).  I do NOT think you need a machine with 8-16 cores. While these can be purchased, you almost certainly do not need a computer with that many cores.

I think virtualization is a good option for you because most of what you need to do can be handled by Ubuntu but there are a few things that you may need to do on Windows. You could install both operating systems in a dual-boot configuration and just reset the computer when you need Windows, but that's a pain in the ****.

In contrast, if you use virtualization, you don't have to reset the computer, you just start Windows while at the same time running Ubuntu. (You get two for the price of one!)

The problem/limitation of this is this eats up system resources. You said in your first post that CPU speed wasn't critical so you could probably get away with a 3 core machine (like having 3 CPUs). You can set it up so Ubuntu will use 2 cores and Windows 1. Most machines today come with 2 cores, and you can easily get desktops/servers with 3-4 cores. Machines with 8 cores or more are expensive and may be well beyond your budget.

You will also need to split your RAM. This is worth more thought if you are running memory intensive operations (for example, databases). Thus you should buy LOTS of RAM so the computer doesn't slow down when you are running both Ubuntu AND Windows. I do this at home on a machine with 8 Gigs of RAM and it works great. At work my computer only has 4 Gigs and I have experiences some slow downs with some operations. If you think you may need to run memory intensive tasks on BOTH windows and Ubuntu at the same time, I would consider getting more than 8 Gigs of RAM, otherwise you will probably be fine with 8.  RAM/Memory - you can never have too much. If you go with 8, make sure the board can handle an upgrade. In a couple of years, 8 may not seem as comfy as it does today.

I hope this clears up any confusion. Seriously - a machine with 8-16 cores is going to cost you big $$$. But if you get one can I borrow/rent some time on it every one in a while?  :-)

---

### Post by nateperson on 2010-01-28
If you truly need 16 cores or more worth of processing power and want a more economical solution, look at a setting up a Cluster.  
It doesn't look like they have good instructions for setting up a cluster specificly on [Ubuntu]("https://wiki.ubuntu.com/EasyUbuntuClustering") yet, but I know there are good walk throughs out for setting one up on lost of different [distros.]("http://ubuntu-utah.ubuntuforums.org/showthread.php?t=516141")

---

### Post by epigram on 2010-01-31
I think these are all good suggestions, but you haven't actually specified your needs.  Some algorithms can not be clustered, several comercial applications may not support clustering, and several tend to have a high variance as to what will typically increase performance.

Let's take for example SAS.  SAS by itself tends to not be very memory intensive, however SAS/IML is, if you use a lot of IML or JMP you probably need a good chunk of ram, however SAS/IML doesn't do multi-core, and SAS by itself without some SAS/CONNECT type hacks doesn't handle multi-core or clusters very well either.  SAS base loves IO like crazy though, a cheap celeron with a SSD and two gigs of ram will probably run most SAS procs faster than a $4000 workstation with a few 7200 rpm hdd's.  

So you really need to profile your work load, generally:

BASE SAS tends to be IO bound, doesn't handle clustering too well.  (clustering is also a lot more money)

R/S/Matlab -tend to eat a lot of ram, generally not IO bound unless your swapping a lot (32gb used of ram not uncommon for large data sets)

JMP - also tends to use ram quite a bit.

I don't use stata or spss much at all, but I'm guessing that their profiles are a bit like R/S/Matlab.


Since you are using Linux, do you plan to have users ssh into the system over a lan from their own workstations, are you planning on hot-seating, or something in between?

Do your windows applications run in wine?

Depending on how you answer these questions, your specs might change quite a bit.  If everyone is running remote X/VNC/ssh off your linux box then you don't need to spend any real money on vide hardware, you might even go headless if you have a nice serial console on your motherboard.

---

