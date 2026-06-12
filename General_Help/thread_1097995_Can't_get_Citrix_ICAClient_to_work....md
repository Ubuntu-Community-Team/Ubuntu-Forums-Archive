---
title: "Can't get Citrix ICAClient to work..."
date: 2009-03-16
forum: General Help
---

### Post by rmburke2 on 2009-03-16
Hi.
I've been trying to get Citrix ICAClient to work for the Ubuntu partition of my work computer in my spare time, and nothing I do seems to help.  I've tried all the advice on the other threads and various places around the internet, but mine doesn't seem to work like everyone else's.  I can get into setupwfc and install, but after it installs I can't do anything with it.  I have icons in my internet tab and a plugin for firefox, but none of them do anything.  I've attached a screenshot so you can see what I'm talking about (not sure how to make it appear here?).  Am I missing something?

---

### Post by gheeke on 2009-03-17
The problem is that you have installed the lastest Citrix ICA Client for Linux Version 11 aka Citrix Receiver. The Citrix Linux Client since Version 11 needs open motif 2.3.1. Ubuntu includes only the prior Version 2.2.3-2. At the moment there are no Debian or Ubuntu packages for open motif 2.3.1 available.

But the following trick *might* help. The solution is unsupported, use at your own risk. 

Install the open-motif package 2.2.3-2. Its included in the libmotif3 package (sudo apt-get install libmotif3) Change to the directory where the library libXM.so.3 is installed (cd /usr/lib). Make a symbolic link from libXM.so.3 to libXm.so.4 (sudo ln -s libXm.so.3 libXm.so.4)
The Citrix Receiver should now open - and hopefully work without further problems.

Another possibility is to use the Linux ICA Client 10.6. That one works with libmotif3 out of the box.

---

### Post by rmburke2 on 2009-03-20
Thanks a bunch, I'm just going to get the earlier version :)

---

### Post by Super Jamie on 2009-03-25
> **gheeke said:**
> sudo apt-get install libmotif3
cd /usr/lib
sudo ln -s libXm.so.3 libXm.so.4

This works great with Citrix 11, thankyou so much.

---

### Post by tin2001 on 2009-03-25
Awesome... Worked for me too. :popcorn:

---

### Post by Bufke on 2009-03-27
Doesn't work for me.  I'm running 64 bit.  getlibs doesn't work either.

---

### Post by riverwhy on 2010-05-27
am having similar problems - have installed icaclient but when i click on the citrix receiver - nothing happens. As suggested above i have installed libmotif3 but being new to ubuntu i i don't get this bit

 "Change to the directory where  the library libXM.so.3 is installed (cd /usr/lib)" 

what EXACTLY do you type in? i tried cd/usr/lib & cd/usr/libXM.so.3 - both times it said "no such file or directory"  ??

---

### Post by gheeke on 2010-05-27
There needs to be a space between cd and /usr/lib. E.g cd /usr/lib and not cd/usr/lib.

---

