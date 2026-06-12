---
title: "Installing kernel image - help"
date: 2009-01-15
forum: General Help
---

### Post by floatingpoint on 2009-01-15
Hey folks,

I'm following a guide to get the Tascam USB-122L working, which is the subject of much discussion over [here]("http://ubuntuforums.org/showthread.php?t=863109") (you'll also find the guide at [http://wiki.briata.org/doku.php?id=testing_us122l_under_linux](http://wiki.briata.org/doku.php?id=testing_us122l_under_linux)).

So anyway I get to the bit where I've to install a new kernel

```
sudo dpkg -i linux-image-2.6.25.4-us122l_1.bri_*.deb
```

And I get a big message saying:

>  You are attempting to install a kernel image (version 2.6.25.4-us122l) However, the directory /lib/modules/2.6.25.4-us122l/kernel still exists.  If this directory belongs to a previous linux-image-2.6.25.4-us122l package, and if you have deselected some modules, or installed standalone modules packages, this could be bad.

If /lib/modules/2.6.25.4-us122l/kernel belongs to a old install of linux-image-2.6.25.4-us122l, then this is your last chance to abort the installation of this kernel image (nothing has been changed yet).

If you know what you are doing, and if you feel that this image should be installed despite this anomaly, Please answer n to the question.

Otherwise, I suggest you move /lib/modules/2.6.25.4-us122l/kernel out of the way, perhaps to /lib/modules/2.6.25.4-us122l.kernel.old or something, and then try re-installing this image. 

Stop install since the kernel-image is already installed?   Y / N? 

And that's where it's sitting right now.

I thought the sensible thing to do would be to ask you lot. The fate of my install is in your hands. What should I do?

---

### Post by Yellow Pasque on 2009-01-15
It appears you've already installed the .deb package in the past. What kernel and distro are you currently using?
```
uname -a
```

---

### Post by floatingpoint on 2009-01-15
Hey Tem,

uname -a tells me I'm using 2.6.27-9-generic. I want to use 2.6.25.4-us122l to get a piece of hardware (the Tascam US-122L) working. 

I went to synaptic and found the us-122l one, marked it for complete removal. I checked /lib/modules, there's a directory called 2.6.25.4-us122l. However, it's empty. I can't delete it.

Tried unpacking again, got the following:

```
kevin@kevin-desktop:/usr/src$  sudo dpkg -i linux-image-2.6.25.4-us122l_1.bri_*.deb
[sudo] password for kevin: 
Selecting previously deselected package linux-image-2.6.25.4-us122l.
(Reading database ... 130566 files and directories currently installed.)
Unpacking linux-image-2.6.25.4-us122l (from linux-image-2.6.25.4-us122l_1.bri_amd64.deb) ...
Done.
Setting up linux-image-2.6.25.4-us122l (1.bri) ...
Running depmod.
Finding valid ramdisk creators.
Using mkinitramfs-kpkg to build the ramdisk.
Running postinst hook script update-grub.
Searching for GRUB installation directory ... found: /boot/grub
Searching for default file ... found: /boot/grub/default
Testing for an existing GRUB menu.lst file ... found: /boot/grub/menu.lst
Searching for splash image ... none found, skipping ...
Found kernel: /boot/vmlinuz-2.6.27-9-generic
Found kernel: /boot/vmlinuz-2.6.27-7-generic
Found kernel: /boot/vmlinuz-2.6.25.4-us122l
Found kernel: /boot/memtest86+.bin
Replacing config file /var/run/grub/menu.lst with new version
Updating /boot/grub/menu.lst ... done

Examining /etc/kernel/postinst.d.
run-parts: executing /etc/kernel/postinst.d/dkms
run-parts: executing /etc/kernel/postinst.d/nvidia-common
run-parts: /etc/kernel/postinst.d/nvidia-common exited with return code 20
Failed to process /etc/kernel/postinst.d at /var/lib/dpkg/info/linux-image-2.6.25.4-us122l.postinst line 1181.
dpkg: error processing linux-image-2.6.25.4-us122l (--install):
 subprocess post-installation script returned error exit status 2
Errors were encountered while processing:
 linux-image-2.6.25.4-us122l

```

What's stopping it?

---

### Post by Yellow Pasque on 2009-01-15
The nvidia-common package is preventing installation. This bug has hit me in the past too (it's still open on Launchpad). My solution was to completely remove/purge the nvidia-common package and then install the kernel package. If you have nvidia hardware, you should probably reinstall the nvidia-common package after you've installed the kernel package.
[https://bugs.launchpad.net/ubuntu/+bug/292606](https://bugs.launchpad.net/ubuntu/+bug/292606)

---

### Post by blazemore on 2009-01-15
It's really straightforward.
Yes it's fine to continue with the installation.
What happened was the first time you tried, it failed with the nvidia-common error.
Now it's giving you "already exists" errors.
What you need to do is ignore the error you're getting now, let it try to install.
It will probably fail with nvidia errors.

Then you run
```
sudo aptitude purge nvidia-common
```
at which point the kernel installation should complete.
Then reinstall it:
```
sudo aptitude install nvidia-common -y
```

This will work.

---

### Post by floatingpoint on 2009-01-16
I just removed nvidia-common in synaptic. This *seems* to have worked; The installation didn't throw up any errors and when I boot up and hit esc for the GRUB menu (i think?) I can select a kernel. 

When I load the us122l kernel, it's like a fresh install. I trust this is common? One major setback is that I can't connect to the net, it seemingly doesn't recognise my wireless adapter, whereas it was recognised immediately when I first installed 8.10. 

**Is it safe to switch between this up-to-date kernel and the one I have just installed? **That way, I can use this for day-to-day stuff and I can switch to the other for recording.

---

### Post by floatingpoint on 2009-01-16
[QUOTE=blazemore]You should post on the thread, so other people can benefit.
Copy your response to it, and I'll copy this reply:

I have no idea why it's like a fresh install, it definately shoudldn't be since all the configuration files are still there.
I could never get wireless working under kernel 2.6.28 and I still haven't worked it out.
Keep hacking, and if you do find a way, let me know![/QUOTE]

I'm pretty new so I doubt I'm likely to work that one out myself.

Is it safe to switch between kernels regularly though? 

And does anyone know how to ensure all the /proc stuff is honoured in the other kernel?



edit-: it may be worth noting that after installing the kernel, it still boots in the most up to date one by default

---

### Post by blazemore on 2009-01-16
To be honest, if you aren't desperate for the new features, compiling a kernel is a bit pointless.

Let's say it takes 80 minutes to compile, and shaves, say, 2 seconds off your boot time.

80 * 60 = 4800 seconds

So in order to get "payback time" you'd have to do approximately 2,400 boots. At one a day, that's 2,400 days or 13 years.

Wait for April, when Jaunty will come out, featuring the 2.6.28 (possibly 2.6.29? Someone check me), and installation-time EXT4 support during manual partitioning.

The only change from 2.6.27 - 2.6.28 is stable ext4, and it was pretty stable anyway.

---

### Post by floatingpoint on 2009-01-16
As mentioned above, I'm installing this kernel to use a certain piece of hardware. An external audio interface to get a decent input to the DAW Ardour.

I have the piece of hardware on loan, to check out Linux for this sort of thing. When I come to purchase my own, I might go for something that's already supported by ALSA (increasingly likely as this debacle goes on), however most of those external devices with preamps are shite (open to suggestions!) and I quite like the US-122L,


Btw, I saw someone post that they had upgraded to Jaunty (9.04, right?) and patched some ALSA-related files, which resulted in the US-122L being recognised, but I was under the impression that, as you say, it doesn't come out 'til March/April time.

---

