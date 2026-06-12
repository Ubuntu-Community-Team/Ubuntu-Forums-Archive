---
title: "Need Help Desperately"
date: 2007-02-10
forum: Desktop Environments
---

### Post by LiquidFlame on 2007-02-10
I recently installed Beryl and it works great.  Today when I turned on my computer it said that I had updates so I installed them.  Once I restarted my computer I noticed when my GRUB stated up that I had another kernel option to chose from.  I guess one of the upgrades was for my kernel.  When I chose the new kernel 2.6.17-11 I got this error

> Failed to start X server.  It's likely that it is not set up correctly.  Would you like to view the X server output to diagnose the problem.

When I clicked yes, I got this output

> X window system version 7.11
            X protocol version 11, Revision 0, release 7.11
            Fatal: Could not open '/lib/modules/2.6.17-11-generic/volatile/nvidia.ko': no such file              
            or directory
            (EE) NVIDIA(0): Failed to load NVIDIA kernel module


I restated my computer and chose the old kernel option 2.6.17-10 and it worked fine, I got into my desktop and everything worked.  What I want to know is what happened and why the updates messed up my system.  Again the bad kernel option was 2.6.17-11.  Any help would be great.  Thanks

---

### Post by Bil-E-daKid on 2007-02-10
Hi there,

The recent updates installed a brand new kernel version.  There are some drivers that require recompiling/reinstalling whenever you install a new kernel.

One example of these is the NVIDIA display drivers, and another is some of the kernel modules that come with freely available VMware Server/Player products.

In any case, just reinstalling your NVIDIA display drivers (however you installed them in the first place) should fix the problem.

Please note that, in order for this to work, you need to have the new kernel running i.e. you'll need to reboot, select the new kernel option and then do the NVIDIA reinstall from the command line.  That being the case, make sure you have the reinstallation instructions available to you before you boot using the new kernel.  (Print 'em out if necessary).

Also, I should add, there may actually be a different (and possibly more user friendly) way of doing this a different way that I am not aware of.

Regards
Bil-E-daKid

---

### Post by familyjules74123 on 2007-09-18
> Please note that, in order for this to work, you need to have the new kernel running i.e. you'll need to reboot, select the new kernel option and then do the NVIDIA reinstall from the command line.  That being the case, make sure you have the reinstallation instructions available to you before you boot using the new kernel.  (Print 'em out if necessary).

where would i find instructions to reinstall nividia drivers from a command line?  Thanks for the help in advance!

---

### Post by Bil-E-daKid on 2007-09-19
Hey there familyjules,

I'd recommend downloading the latest NVIDIA drivers from nvidia.com before you restart, and also make sure you have installed the 'build-essential' like this (from a command line):

sudo apt-get install build-essential

Then, once you've restarted and X most likely doesn't start, log in to the command line and then change to the directory you have the downloaded drivers in and type this:

sudo sh ./<name-of-nvidia-download>

That should start the NVidia installer and it'll do the rest for you - just follow the text mode wizard through to completion.

As originally stated, there may actually be a different (and possibly more user friendly) way of doing this a different way that I am not aware of.

HTH
BEdK

---

### Post by dondad on 2007-09-20
> **LiquidFlame said:**
> I recently installed Beryl and it works great.  Today when I turned on my computer it said that I had updates so I installed them.  Once I restarted my computer I noticed when my GRUB stated up that I had another kernel option to chose from.  I guess one of the upgrades was for my kernel.  When I chose the new kernel 2.6.17-11 I got this error



When I clicked yes, I got this output



I restated my computer and chose the old kernel option 2.6.17-10 and it worked fine, I got into my desktop and everything worked.  What I want to know is what happened and why the updates messed up my system.  Again the bad kernel option was 2.6.17-11.  Any help would be great.  Thanks

If you install the nvidia drivers with Envy or yourself, X will break on kernal updates. Install the driver through the repos with the restricted driver manager and it should work through updates.

---

### Post by Bil-E-daKid on 2007-09-20
Thanks for that dondad - I was not aware of that.

---

