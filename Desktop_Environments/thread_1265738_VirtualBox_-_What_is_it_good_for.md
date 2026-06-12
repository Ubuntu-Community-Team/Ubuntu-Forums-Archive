---
title: "VirtualBox - What is it good for?"
date: 2009-09-13
forum: Desktop Environments
---

### Post by GroogFish on 2009-09-13
I just found this virtualbox thing and it looks really cool but I'm not if it has any practical purposes. I have several questions about it and hope some of you can answer them.

1. What is it good for? (Very broad question, I know).

2. I already have part of my drive partitioned for windows xp. Would having a virtual machine of it just be redundant?

3. Is this an emulator?

4. Will this be a lot slower then the operating system itself?
-If not, will it be faster since it's running on linux?

5. Will games work on it (well)? I've partitioned part of my drive for windows for, you've guessed it, games. Will games run the same on the virtualbox?

6. How will this affect me drive? I just created a 10gig partition in the virtual box. How will this affect my hard drive?

Thanks for your help!

---

### Post by noelvh on 2009-09-13
> **GroogFish said:**
> I just found this virtualbox thing and it looks really cool but I'm not if it has any practical purposes. I have several questions about it and hope some of you can answer them.

1. What is it good for? (Very broad question, I know).

2. I already have part of my drive partitioned for windows xp. Would having a virtual machine of it just be redundant?

3. Is this an emulator?

4. Will this be a lot slower then the operating system itself?
-If not, will it be faster since it's running on linux?

5. Will games work on it (well)? I've partitioned part of my drive for windows for, you've guessed it, games. Will games run the same on the virtualbox?

6. How will this affect me drive? I just created a 10gig partition in the virtual box. How will this affect my hard drive?

Thanks for your help!

Well I have been using VB for years, and love it. So I will answer based on how I use it. I have a system that is single boot to Ubuntu 9.04, with a VB for windows XP FLP version. 
1) For me it allows me to help windows users (fiends and family) with out having to reboot or get off my *** and go to my desktop. Also I use it for testing windows apps. I also like to test drive other Linux distros with having to install or reboot my system.
2) No you just don't have to reboot.
3) I don't have a good answer for this one but I would say no!
4) That is based on the system you are using. I have a P4 1.86 2gb ram and it runs both very well.
5) This is why I keep a XP desktop. I am sorry XP dose games better for me.
6) the HD you create in VB is just a file, and will have no effect other than it takes up space on your hadrdrive.

I hope this helps

Noel

---

### Post by GroogFish on 2009-09-13
Thanks for your reply. I've gotten windows xp on a virtualbox right now but the drivers aren't installed. Is it a good idea to install drivers to a virtual machine?

---

### Post by Whiffle on 2009-09-13
You don't need drivers for your real computers hardware, since the OS running in the virtual machine doesn't actually see that hardware.  It is a good idea to install the VirtualBox Guest Additions though, I think its under the mount menu..

---

### Post by theZoid on 2009-09-13
Yes, forget the drivers because it uses simulated hardware, but definitely isntall guest additions or you'll miss out on some great features!  I run my work programs in VB and have USB enabled to print, scan, etc....for USB don't use the VB OSE from the repos, go to the Sun website and download VB.

---

### Post by andrew.46 on 2009-09-14
Hi GroogFish,

> **GroogFish said:**
> What is it good for? (Very broad question, I know).

It took me a fair bit of distro-hopping to realise that no matter how many distros you have on your system there is only one *primary* distro which you use for your day today computer needs. VirtualBox fits this picture perfectly where you have a host system to get things done with and any number of guest systems available* without* rebooting. These guest systems can be for curiosity and experimentation, for troubleshooting questions on different versions of a distro, for access to specialised software not available to the primary distro etc. Lots of scope for a huge amount of fun :).

Andrew

---

### Post by earthpigg on 2009-09-14
in addition to what others have said:

if you ever want to try something completely off the wall with Ubuntu or any other operating system ("i wonder that that infamous *rm -ri /* command actually looks like when run...."), VBox gives you a sandbox to do this in without risking anything.

its a playground where you can simulate Nuclear Holocaust without actually risking anything.


or so you think! [http://en.wikipedia.org/wiki/WarGames](http://en.wikipedia.org/wiki/WarGames)



(yes, i know that isn't actually "the infamous command" above.)

---

### Post by 3rdalbum on 2009-09-14
> **GroogFish said:**
> I just found this virtualbox thing and it looks really cool but I'm not if it has any practical purposes. I have several questions about it and hope some of you can answer them.

1. What is it good for? (Very broad question, I know).

Too much to explain. The most common use is to test new distributions and operating systems. I'm just going to try Haiku Alpha 1 in it.

I use 64-bit Ubuntu as my main distribution, but when I want to compile a package for 32-bit I start up a 32-bit virtual machine and compile in there.

People in computer support help desks don't have to have five computers in front of them so they can provide support for Windows 2000, XP, Vista, Mac OS X, and Linux. They just run five virtual machines, each with a different guest operating system, so they can walk their customers through a procedure precisely.

With certain kinds of servers, virtual machines are fantastic. Traditionally it's a good idea to keep your database server on a different machine to your mail server, or your web server; but this uses up lots of power. So they virtualise the database server, mail server and web server on the same machine, so they can't interfere with eachother. When that machine starts to get fully loaded from these three servers in the VMs, then they boot up another computer, "migrate" one of the VMs to the other computer, and everything continues with no downtime.

Those are just some of the uses.

> 3. Is this an emulator?

4. Will this be a lot slower then the operating system itself?
-If not, will it be faster since it's running on linux?

There is no emulated CPU. Instructions get sent from the VM to the CPU with little modification, which makes it fast. I think the general figure is 90% of the bare-metal speed? Some CPUs have hardware features to support virtualisation, which mean that less modification needs to be done to the instructions in order for the CPU to accept them, which means a further speed increase.

Hardware devices are emulated. You can't have multiple operating systems trying to access the sound card simultaneously; that's a recipe for disaster. So hardware device access is moderated by the host OS.

> 5. Will games work on it (well)? I've partitioned part of my drive for windows for, you've guessed it, games. Will games run the same on the virtualbox?

You can't have multiple operating systems accessing the graphics card simultaneously. There is graphics card emulation available in Windows guests and Linux hosts, but I never got it working, and I believe it depends on some code from Wine.

> 6. How will this affect me drive? I just created a 10gig partition in the virtual box. How will this affect my hard drive?

Do you mean that you used the Virtualbox program to create a 10 gigabyte virtual hard disk? If so, then that hard disk is just a file sitting on a real hard disk.

If you mean that you used a partitioning program running inside a virtual machine, then it has only created the partition on the virtual drive, which is just a file sitting on a real hard disk.

---

### Post by steveneddy on 2009-09-14
VirtualBox or VMware are virtual machines (VM's)

a **virtua**l or software** box**, or **machine** to install an operating system on

Software that replicates hardware

[Look here]("http://www.virtualbox.org/wiki/VirtualBox")

---

