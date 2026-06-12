---
title: "Kernel Upgrade Broke X"
date: 2006-09-19
forum: Desktop Environments
---

### Post by aay on 2006-09-19
I know there have been problems with Kernel upgrade breaking X, but I thought these had been fixed.  The upgrade alert tool in Ubuntu showed me that that there was an update available to the 2.6.15-27 and I upgraded a few minutes ago.  After rebooting X would not start.  Why does this keep happening?  Surely I can't be the only one.  These sorts of incidents are going to run a lot of new folks away from Ubuntu/Linux.  There was no fix available after doing an update/upgrade.

I pretty much realized that this was Nvidia related and I had a backup of my old xorg.conf before installing the Nvidia drivers.  I grabbed the backup and overwrote my xorg.conf with it and now X starts fine so I was able to fix the problem.  How many new people are going to know how to do this though?  I guess I'll go and reinstall my Nvidia drivers now.

I really, really hope these sorts of problems can be eradicated.

Adam

---

### Post by wkulecz on 2006-09-19
+1, you are 100% correct.

I've found every Debian based distro I've tried (Knoppix, Debian, and now Ubuntu) to be fragile with respect to updates.

Maybe there is an issue with repository syncing as some folks get mis-matched versions as the "latest".  I guessing, but something needs to be done.

I was bit badly and wasted pretty much the whole day with last week's "kernel update".

I've ignored todays "updates ready" message.  Seems to have been a good thing!

Actually all you probably had to do was change Driver "nvidia" to "nv" in xorg.conf in case you'd made other changes since you last xorg.conf backup.  I got my system back up quicky, but its useless to me without the xvidia drivers as the nv driver has a serious performance regression with the Xvideo extensions.

Fedora Core 5 has fixed the issue, although the nvidia drivers on Ubuntu use only about 7% cpu, compared to the ~28% FC5 nv driver uses when running my app according to "top".  Both are adaquate, but the 92+% of the Ubuntu nv driver is a showstopper!

--wally.

---

### Post by rickg on 2006-09-19
Same here. Look Ubuntu folks... LTS is NOT supposed to mean Long Term Screwups. Once was human error - happens to us all. But what is this, the 3rd  update in six weeks to result in people's inability to actually run their machines? 

Can I edit Xorg.conf to fix this? Probably... But let's stop all of the annoying talk about Bug #1 being MSFT's dominance until we get our own house in order re stability, eh?

---

### Post by someguyouknow on 2006-09-19
i think if you use nvidia-glx drivers, the problem wont happen...
the last few updates went without a hitch for me...

---

### Post by kick6 on 2006-09-19
Is the nvidia-glx package in an official repository or is it a universe/multiverse package?

---

### Post by someguyouknow on 2006-09-19
not sure... i think i used automatix to get the drivers...

i think with the other drivers, you have to update the kernel and then install the drivers on top of that...

---

### Post by cmost on 2006-09-19
I can report that I upgraded my K7 version of the kernel, kernel headers, restricted kernel modules and nvidia-glx yesterday without issue.  I will say that VMware had to be recompiled before it would run but no other issues.  Perhaps this problem is isolated to certain kernel packages or certain arch's and won't affect the populaton at large (as was the case with the xorg update fiasco a few weeks ago.)

Considering the extensive breadth of PC hardware on the market, especially that which supports Linux (remember, Microsoft refuses to support hardware outside its minimum system requirements) I think Ubuntu's track record is golden with regards to compatibility and updates.  Another consideration is the fact that F/OSS packages are nearly always moving targets.  Under such circumstances, its unrealistic to expect 100% stability 100% of the time.  The only way you're going to maintain that kind of stability is to configure your system the first time, lock it down, and refuse all subsequent updates.  This way your system will remain frozen in the same state.  Good luck.

---

### Post by kick6 on 2006-09-19
I think where people are having the most problems is that they've installed the nvidia drivers using something other than aptitude.  Therefore, the update-manager doesn't know it needs to update that kernel module when it updates everything else.

---

### Post by aay on 2006-09-19
> **kick6 said:**
> I think where people are having the most problems is that they've installed the Nvidia drivers using something other than aptitude.  Therefore, the update-manager doesn't know it needs to update that kernel module when it updates everything else.

Well I installed with apt, but yes I did use Automatix.  I can understand how the Ubuntu devs don't feel responsible for things like this.  After all, I did install using a third party tool and non official repositories, blah, blah, blah.  

However I think that some simple things could be done to help people with X problems like myself and others.  Ubuntu should have a procedure in place so that if an upgrade breaks X, something like the following would happen.

1.  During the initial install a backup copy of xorg.conf should be stored somewhere and if xorg fails to start, then the system should revert to the original xorg.conf file.  In my case, although this would not have gotten my Nvidia drivers back, it would have least gotten me back into X.

2.  If the above fails, then Ubuntu should automatically attempt to reconfigure X running something like "dpkg-reconfigure xserver-xorg".  Setting up a procedure where these two things were done if X failed to start would fix the vast majority of people's problems.  

Thoughts from any others?

---

### Post by coffeecat on 2006-09-19
> **kick6 said:**
> I think where people are having the most problems is that they've installed the nvidia drivers using something other than aptitude. 

Nope. Never used aptitude in my life, but the latest kernel upgrade has caused me no problems at all on my desktop (nvidia) and laptop (Intel graphics).

All the proper howtos tell you to make sure you have installed the kernel headers, restricted kernel modules and nvidia-glx. When a new kernel is made available, the update manager or Synaptic will update them all and you should have no problems. I certainly haven't.

At least not yet. :? :wink:

---

### Post by wkulecz on 2006-09-19
I used method 1) from the link below initially and was hit by last week's problem, which was a broken set of packages, not an apt usage error.

[http://doc.gwos.org/index.php/Latest_Nvidia_Dapper](http://doc.gwos.org/index.php/Latest_Nvidia_Dapper)

The fact that there are *three* methods proves there is a design problem.

I don't know what this week's problem really is yet because I was "smart" enough to skip the update when offered this morning.


It looks like in our quest for "easy" we are getting as bad as microsoft -- why are there so many ways to update a driver in windows, and how are you supposed to know which one to use?  Ever been bit by the bug where you installed the hardware first and booted expecting a prompt for a driver install and instead windows installed a broken driver which prevents installing the correct driver?  Of course a readme file somewhere on the driver CD said to "install the drivers first" but when driver CDs contain dozens of drivers for hardware you don't have it gets to be a confused mess fast.

--wally.

---

### Post by kick6 on 2006-09-19
> **coffeecat said:**
> Nope. Never used aptitude in my life, but the latest kernel upgrade has caused me no problems at all on my desktop (nvidia) and laptop (Intel graphics).

All the proper howtos tell you to make sure you have installed the kernel headers, restricted kernel modules and nvidia-glx. When a new kernel is made available, the update manager or Synaptic will update them all and you should have no problems. I certainly haven't.

At least not yet. :? :wink:


how is it you didn't use aptitude, but installed restricted kernel modules?  Restricted kernel modules doesn't *mean* anything outside of the debian package system.

---

### Post by coffeecat on 2006-09-20
> **kick6 said:**
> how is it you didn't use aptitude, but installed restricted kernel modules?  Restricted kernel modules doesn't *mean* anything outside of the debian package system.

How long have you been using Ubuntu? Ever heard of apt-get or Synaptic? :roll:

---

### Post by ebash on 2006-09-20
I think that there should be a way to specify a list of X drivers to try.
This way if some fancy driver like the nvidia driver fails X could probe the nv drivers and the vesa drivers.

This way the end users will be presented with a graphical interface that will let them upgrade and fix their system once the X packages are fixed. Instead of having a scary blue screen of death.

---

### Post by tofuconfetti on 2006-09-20
This really is getting a little frustrating. What happened to me is that the kernel upgrade went fine, the "linux-restricted-modules common" gets upgraded fine, but the linux-restricted-modules 2.6.15-26-k7 didn't get upgraded, so there was no nvidia.ko module to be loaded.  Thus, when I rebooted X would not start.  The only reason I knew what this probably was is that I had to solve this from the last time they messed the kernel upgrade up.

---

