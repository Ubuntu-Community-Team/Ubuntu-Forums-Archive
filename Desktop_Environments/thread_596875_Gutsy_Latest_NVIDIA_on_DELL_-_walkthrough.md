---
title: "Gutsy Latest NVIDIA on DELL - walkthrough"
date: 2007-10-30
forum: Desktop Environments
---

### Post by gtdaqua on 2007-10-30
[B]
UPDATE: Applies for Ubuntu 8.04 "Hardy Heron" too. Tested and working.
[/B]
After running into several problems and searching for solutions to get the latest NVIDIA driver working, I decided to post it.

It applies for both 32 and 64 bit because I have tested on both - multiple times.

So you have installed Gutsy 7.10 and done all the 'apt-get install update' and 'upgrade'.
Download the latest NVIDIA driver (currently 100.14.23) and save it to your home folder.

Now here's the trick. Enabling Ubuntu's restircted drivers will install NVIDIA but when u restart the GUI will be gone! So DO NOT install the NVIDIA driver from the restricted driver manager. I'll show you how to install manually.

Here are the prerequisites:
You need the kernel source so that NVIDIA can compile the drivers for your running kernel. You can get this info by typing
```

uname -r

```
General belief is that you can get the kernel sources by typing 
```

sudo apt-get install linux-headers-`uname -r` 

```

But this wasnt quite enough for nvidia. So you have to install the linux-restricted-modules for your kernel.
```

sudo apt-get install linux-restricted-modules-`uname -r`

```

And you need linux-source as well. This can be installed from Adept Manager or Synaptic. It would look like "linux-source-2.6.22". The description would say that you dont need because the source would be provided by linux-headers. But install anyway. No harm.

So, in short you need:
linux-headers-`uname -r`
linux-source-2.6.22 (better install from synaptic)
linux-restricted-modules-`uname -r`
build-essential (do sudo apt-get install build-essential)

Then run the following: use "kdm" in place of "gdm" if you are using Kubuntu.
```

sudo /etc/init.d/gdm stop

```

Press ctrl+al+f1 and login using root account.
Navigate to the location where you saved the latest NVIDIA driver.
run the program;
```

chmod a+x NVIDIA-Linux-x86-100.14.23-pkg1.run
sh NVIDIA-Linux-x86-100.14.23-pkg1.run

```

Choose defaults and finish the installation. Once you are back in the terminal you have to do the most important thing. Now we dont need restricted modules or linux-sources because Ubuntu will try to use them during startup of NVIDIA and your GUI will fail. To prevent this from happening edit the following file
```

nano /etc/default/linux-restricted-modules-common

```

The last line would look like this

```

DISABLED_MODULES=""

```

Change it to reflect this:
```

DISABLED_MODULES="nv nvidia"

```

Now we are preventing Ubuntu to load its own NVIDIA modules (I am not sure how exactly to explain this).

Now restart the GDM or KDM.
```

sudo /etc/init.d/kdm start

```

You should see the NVIDIA logo and then the login screen! Restart the machine to see if NVIDIA logo is coming without interruption and you are not shown any white cursor or a blank screen!

---

### Post by Crafty Kisses on 2007-10-30
> **gtdaqua said:**
> After running into several problems and searching for solutions to get the latest NVIDIA driver working, I decided to post it.

It applies for both 32 and 64 bit because I have tested on both - multiple times.

So you have installed Gutsy 7.10 and done all the 'apt-get install update' and 'upgrade'.
Download the latest NVIDIA driver (currently 100.14.23) and save it to your home folder.

Now here's the trick. Enabling Ubuntu's restircted drivers will install NVIDIA but when u restart the GUI will be gone! So DO NOT install the NVIDIA driver from the restricted driver manager. I'll show you how to install manually.

Here are the prerequisites:
You need the kernel source so that NVIDIA can compile the drivers for your running kernel. You can get this info by typing
```

uname -r

```
General belief is that you can get the kernel sources by typing 
```

sudo apt-get install linux-headers-`uname -r` 

```

But this wasnt quite enough for nvidia. So you have to install the linux-restricted-modules for your kernel.
```

sudo apt-get install linux-restricted-modules-`uname -r`

```

And you need linux-source as well. This can be installed from Adept Manager or Synaptic. It would look like "linux-source-2.6.22". The description would say that you dont need because the source would be provided by linux-headers. But install anyway. No harm.

So, in short you need:
linux-headers-`uname -r`
linux-source-2.6.22 (better install from synaptic)
linux-restricted-modules-`uname -r`
build-essential (do sudo apt-get install build-essential)

Then run the following: use "kdm" in place of "gdm" if you are using Kubuntu.
```

sudo /etc/inid.d/gdm stop

```

Press ctrl+al+f1 and login using root account.
Navigate to the location where you saved the latest NVIDIA driver.
run the program;
```

chmod a+x NVIDIA-Linux-x86-100.14.23-pkg1.run
sh NVIDIA-Linux-x86-100.14.23-pkg1.run

```

Choose defaults and finish the installation. Once you are back in the terminal you have to do the most important thing. Now we dont need restricted modules or linux-sources because Ubuntu will try to use them during startup of NVIDIA and your GUI will fail. To prevent this from happening edit the following file
```

nano /etc/default/linux-restricted-modules-common

```

The last line would look like this

```

DISABLED_MODULES=""

```

Change it to reflect this:
```

DISABLED_MODULES="nv nvidia"

```

Now we are preventing Ubuntu to load its own NVIDIA modules (I am not sure how exactly to explain this).

Now restart the GDM or KDM.
```

sudo /etc/init.d/kdm start

```

You should see the NVIDIA logo and then the login screen! Restart the machine to see if NVIDIA logo is coming without interruption and you are not shown any white cursor or a blank screen!
Thanks!

---

### Post by spalVl on 2007-12-17
I had to compile a custom kernel on Gutsy to get apply a patch and the restricted drivers wouldn't work afterwards.  I used this howto to re-setup nvidia drivers after custom kernel and worked fine.  

Thanks!!!

---

### Post by aheitzmann on 2008-02-18
Hi. I've been using ubuntu for a few months, and have not been able to get my graphics card (nvidia nvs quadro 110M) driver working yet. This walkthrough appeared to be just what I needed, but alas, I'm still having trouble. Here's what happened:
-Installation of the packages you recommended went fine - I have all four.
-"sudo /etc/init.d/gdm stop" seems to work, although sometimes it brings me to the fullscreen terminal, and sometimes it just says "stopping gdm..." in the terminal I'm in
-when I ran the installer, I got the error "It appears that you have an X-Server running. Please exit X," or something like that. 
-After fiddling for a while, i.e. killing all the processes with x in the name :( (there must be a better way) I got it to work. 
-Installer tells me it can't find a kernel, and will compile one - this process seems to succeed.
-Installer updates  the xorg.config file
-I put "nv nvidia" in the DISABLED_MODULES field, as specified
-"sudo /etc/init.d/gdm start" starts gnome, which will only run in low graphics mode because the system isn't configured correctly somehow. 

Does anyone have any ideas? If more info is needed about the problem let me know how to get it. I don't even know how to revert to my previous settings since I did all of this manually.
Thanks in advance. 

Alex

---

### Post by gtdaqua on 2008-03-11
what distro are u running?

most should work.  you can try this:

reboot the machine and press 'Esc' to enter GRUB menu. Choose recovery mode. 
remove all NVIDIA modules:

```

sudo apt-get remove nvidia*

```

and run the installer again (follow the guide).

---

### Post by sloggerkhan on 2008-03-11
Hmm... it sounds like it's actually easier to install the latest ati fglrx driver, lol.
lol, I just got my first nvidia card, but I think I'm just using the repo driver instead of installing the latest one. On my laptop I installed the new fglrx driver every month, though.
For ati, you just type one command that makes *.deb files for you that you can just click to install. (of course it's best to rid yourself of the previous drivers first.)

---

### Post by Kiri on 2008-03-12
I can't actually get the nvidia drivers to install. When I try to run the NVIDIA driver package it tells me that X server is still running.
I tried to type "init 3" which did nothing. I tried "init 1" but then I cannot seem to run the package at all, and cannot even find the desktop dir. 

How can I stop the X server and install the drivers?

---

### Post by gtdaqua on 2008-03-13
Kiri,
If u are using ubuntu then its probably GNOME (gdm)

type this:
```

sudo /etc/init.d/gdm stop

```

then press Ctrl+Alt+F1 to access terminal directly and install the NVIDIA driver. 

If you are using Kubuntu, the you have to stop KDE.

type this:
```

sudo /etc/init.d/kdm stop

```

then press Ctrl+Alt+F1 to access terminal directly and install the NVIDIA driver.

---

### Post by aheitzmann on 2008-03-13
oops! Thanks for the response gtdaqua, but you're barely too late - I gave up and uninstalled a few days ago. I'll keep that in mind if I try again in the future though.

---

### Post by Jenxie on 2008-05-07
This howto worked the best, everythings correct except that when i reboot into desktop i see the nvidia logo, boots into desktop and gdm seems to hang, i can move the cursor but can't see the icons and background (black), i can see the clock but not the power button etc =/

Ubuntu 8.04
GeForce 8800GTX
nVidia Drivers 169.12

EDIT: Well i found the simple solution, 169.12 doesn't simply work with 8800GTX on Hardy. So i downloaded [http://www.nvidia.com/object/linux_display_archive.html](http://www.nvidia.com/object/linux_display_archive.html) an newer version (yah, obvious choice -> the archives) and it works flawlessly now. Thx for the gr8 howto.

---

### Post by smooth1988 on 2008-05-11
Hi all,

I followed the guide till i had to push ctrl+alt+f1 and got into a black and white screen. There i had to go to the home directory....

how can i get there? it sounds so stupid.

I am really trying here but Ubuntu is not as user friendly as it claims to be. I am losing hope here :)

Tnx in advance.

Robert

---

### Post by Mohonri on 2008-05-19
Thanks for the guide!  The latest driver from nVidia didn't work, but an older driver (in my case, the 100.14.19 drivers) did.  I also ran into a driver bug that corrupts the display, but restarting X fixed that, at least temporarily.  Having finally achieved some success, I'm gonna leave the shaky driver intact for now.  If it becomes a problem, I'll move up one driver release.

BTW, I'm running a GeForce 6200 128MB AGP.

---

