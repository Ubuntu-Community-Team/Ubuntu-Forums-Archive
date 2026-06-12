---
title: "X locking up system"
date: 2011-02-04
forum: Desktop Environments
---

### Post by vortmax on 2011-02-04
I'm having an odd problem with my Kubuntu Lucid install.  I first started experiencing it when I would leave my computer logged in overnight.  I would come in and find the screen frozen and flickering.  When I ssh'd into the machine, I could see that Xorg was using 100% of the CPU and a ton of memory.  I could kill kdm, but not Xorg.  Only a full reboot would cure it.

When it would reboot, my second monitor sometimes would not work and it would take several reboots to get it up and running.  Recently, I was working in matlab and had Xorg freeze on my numerous times...always when I had my second monitor up and running.

I have checked the logs and don't have any major failure type errors.  The only ones that stand out are:

```

(EE) NVIDIA(GPU-1): Failed to initialize the NVIDIA graphics device PCI:3:0:0. 
(EE) NVIDIA(GPU-1):     Please see the COMMON PROBLEMS section in the README for
(EE) NVIDIA(GPU-1):     additional information.
(WW) NVIDIA(GPU-1): Failed to initialize NVIDIA graphics device on GPU PCI:3:0:0!
(II) NVIDIA(0): Initialized GPU GART.
(II) NVIDIA(0): Setting mode "nvidia-auto-select+0+0"

```

```

root@Sierra:/var/log# cat /dev/nvidia0
cat: /dev/nvidia0: Input/output error

```


The card in question is an Nvidia 9800 GX 2.

It almost seems like GPU0 (the one running the second monitor) is dead or dieing and is causing instability when it is up and running....but I've also heard that X running away and locking up the system is a known bug.

Any thoughts on where to look next?

---

### Post by inobe on 2011-02-04
i believe it's hardware related, pull out the card and clean the dust out of the fan and heatsink.

---

### Post by vortmax on 2011-02-05
To see if it was the card, I swapped it out with a spare I had, which didn't solve the problem.  So I decided to try and upgrade the nvidia drivers to see if that would help.  After downloading the latest version off of nvidia's site, and purging current nvidia drivers and related software from my system, I attempted to install them.

Everything installed fine, but when the system goes to load the kernel module, it does not exist.  I've searched around and found that this is an issue with the kernel, but cannot find a solution.

I've tried reinstalling the drivers from the repos and everything.  Everytime I start X, I get a "FATAL: Module nvidia not found".  If I link or copy the actual kernal module (e.g. nvidia-current.ko) to nvidia.ko, when I manually run modprobe it spits back:

```

FATAL: Error inserting nvidia (/lib/modules/2.6.32-28-generic-pae/updates/dkms/nvidia.ko): Cannot allocate memory

```

and on boot, still gives the same old "FATAL: Module nvidia not found" error.


I'm out of ideas on how to fix this.  I'm running the vesa drivers now, which means I can't run my second screen.  Anyone get the nvidia drivers on lucid to work?

---

### Post by vortmax on 2011-02-07
I just spent the better part of 2 days fighting this, so I thought I would update this post so that others may not go through the same problems.

First off:  The problem I was having to begin with was the card fighting the kernel.  Since the 9800GX 2 is an onboard SLI card, it attempts to initialize 2 cards...but the kernel only reserves enough memory for one.  So I just had to add:

```

vmalloc=256M

```

to my kernel boot params, and all is well.

Now...The NVIDIA driver HELL I went through.  It's not NVIDIA's fault at all, it's the nouveau drivers that are part of the default install.  In summary, what I did was (all in console with no X running):

1. purge the system of all old nvidia drivers (apt-get --purge remove nvidia-*)
2. purge all nouveau packages from the system
3. clean the boot image (sudo update-initramfs -u)
4. appended the following to /etc/blacklist.conf

```

blacklist vga16fb
blacklist nouveau
blacklist rivafb
blacklist nvidiafb
blacklist rivatv

```
5. rebooted and installed the nvidia drivers off their page ([http://www.nvidia.com/Download/index.aspx?lang=en-us](http://www.nvidia.com/Download/index.aspx?lang=en-us))

---

### Post by gmargo on 2011-02-07
> **vortmax said:**
> I would come in and find the screen frozen and flickering.  When I ssh'd into the machine, I could see that Xorg was using 100% of the CPU and a ton of memory.  I could kill kdm, but not Xorg.  Only a full reboot would cure it.


I have had the same problem with an Nvidia GTS 450.  Xorg at 100%, could not be killed.  Even "halt" does not quite halt the machine - I have to use the power switch.

The machine comes back up ok.  I've only had this happen 3 times in the 4 months I've had this setup, but it's quite frustrating!

I'm currently using the latest stable Nvidia driver installed from this ppa:
[https://launchpad.net/~ubuntu-x-swat/+archive/x-updates]("https://launchpad.net/%7Eubuntu-x-swat/+archive/x-updates")

How did you find out about "vmalloc" and what is that really doing?

---

### Post by vortmax on 2011-02-07
I found it by google searching:
 
"ubuntu NVIDIA: could not open the device file /dev/nvidia0 Input/output error)."

which was an error I was receiving while checking the card with nvidia-settings.

What was happening is that by default, the 32 bit kernel wasn't allocating enough memory to the video card, which was making it run funny and preventing the second GPU from functioning.  The vmalloc flag tells the kernel to increase the the amount of memory it allocates to the video cards to 256M.  

I haven't had the system running long enough to see if the Xorg thing is gone or not, but this has improved the stability of my second monitor.

---

### Post by gmargo on 2011-02-07
Here's the error from my logs when it locked up.  I got two of these, two seconds apart.

```

NVRM: os_schedule: Attempted to yield the CPU while in atomic or interrupt context

```

---

### Post by vortmax on 2011-02-07
I had those same errors as well as a handful of others.  I just checked my syslog and since adding the vmalloc line (and installing the latest drivers), I have zero NVRM lines.

just try it and see if it works.  If it doesn't, just change it back.

---

### Post by markthekdeguy on 2011-02-07
remember REISUB will help a more graceful reboot if it all locks
most this Ubuntu pdf cheat sheet is still valid
[http://fosswire.com/post/2008/04/ubuntu-cheat-sheet/](http://fosswire.com/post/2008/04/ubuntu-cheat-sheet/)

---

### Post by gmargo on 2011-02-08
> **vortmax said:**
> 
```

vmalloc=256M

```
According to the Nvidia release notes, vmalloc is only an issue on 32-bit systems.  (My 64-bit system is using 355M according to /proc/meminfo.)

---

### Post by vortmax on 2011-02-08
Didn't know you were on a 64 bit machine, and no..that should not be the problem.  Regardless, try "dmesg|grep alloc" and see if you are getting memory allocation errors.

I did do some more searching around and found some references that claimed the nouveau drivers continued to muck up X if they were installed along side the nvidia drivers (even if the nvidia drivers are active).  You might try purging and blacklisting nouveau and installing the newest drivers from Nvidia's site (260.16.36).  You'll have to recompile/install them every time you upgrade the kernel, but that's not too bad.

---

### Post by vortmax on 2011-02-14
Just an update.  Since updating the driver, I have neither shutdown nor logged out of the machine and it continues to be running stable with no errors being logged.

So one of three things fixed it:

1. Upgrading to the 260 drivers
2. Completely ditching nouveau
3. Fixing the memory allocation problem in the kernel

---

### Post by vintermann on 2012-04-10
> **gmargo said:**
> Here's the error from my logs when it locked up.  I got two of these, two seconds apart.

```

NVRM: os_schedule: Attempted to yield the CPU while in atomic or interrupt context

```

Similar situation here, screen flickers or goes black, everything locks up. Last messages in syslog from before I had to force a reboot was four of those lines.

I lost hours of work due to this bug :mad:

This is a laptop, 64-bit Oneiric, with a Nvidia GeForce GTX 285M. Exactly which driver is in use I'm a bit unsure of; the "additional drivers" app lists 4 drivers with identical descriptions: "version current [recommended]", "version 173", "version 173-updates" and "post-release updates version current updates". I use the first of those.

I've purged noveau for now and crossing my fingers. I definitively do not want to do manual downloads and lots of work every time there is a kernel update.

---

### Post by oldos2er on 2012-04-10
Closed. Please start a new thread; this one's over a year old.

---

