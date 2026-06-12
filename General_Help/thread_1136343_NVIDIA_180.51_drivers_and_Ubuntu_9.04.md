---
title: "NVIDIA 180.51 drivers and Ubuntu 9.04"
date: 2009-04-24
forum: General Help
---

### Post by dmillerw on 2009-04-24
I've been attempting to install the NVIDIA drivers for Ubuntu, but have been failing. Whenever I try, it seems like it installs, but when I reboot, it boots into low graphics mode and gives me these errors.

(```
EE)Failed to load module "type1"
(EE)Failed to load module "freetype"
(EE)NVIDIA(0) Failed to initalize the NVIDIA kernel module
``` 

It then goes on to say, please ensure you have a compatible NVIDIA GPU installed, yada yada yada, the card did work in 8.10

---

### Post by dmillerw on 2009-04-25
Anyone?

---

### Post by michael.fries on 2009-04-26
Same for me.

---

### Post by UranUtan on 2009-04-26
Got same problem but solved it "accidentally". I have noticed the Update Manager was broken, the "Partial Upgrade" couldn't complete. May be this left the system with something inconsistent to download other updates.

I saw in another post you need to complete the online update manually like that
```
sudo apt-get dist-upgrade
```
In my case I have to attemp several times to succeed. You will see by the feedback in the terminal whether the operation is succeddful or not. After that, I just went to System / Admin / Hardware Drivers. And selected NVIDIA accelerated graphics driver (version 180) then click activate. This time the driver is downloaded and installed OK.

Good lucks.

---

### Post by Teh H4rRy on 2009-04-26
I dont know if this applies for me but the hardware drivers installer tool gives be version 96 to install. I install this reboot and the drivers dont work and ubuntu runs in low graphics mode. I really want some working drivers, Ubuntu doesnt look good in 800x600 on a 22" display:(

EDIT: I installed the drivers, it nagged, ran in low graphics mode, i have my higher resolution but scrolling and moving things around is very juttery, and i cannot enable desktop effects. I go to open display properties and the (Nvidia X server settings) dialouge pops up. Then i am prompted "You do not appear to be using the NVIDIA X driver. Please edit your X configuration file (just run `nvidia-xconfig` as root), and restart the X server. " I do so in terminal and this happens.

> harry@ubuntu:~$ nvidia-xconfig

Using X configuration file: "/etc/X11/xorg.conf".

WARNING: No Layout specified, constructing implicit layout section using screen
         "Default Screen".


WARNING: Unable to find CorePointer in X configuration; attempting to add new
         CorePointer section.


WARNING: The CorePointer device was not specified explicitly in the layout;
         using the first mouse device.


WARNING: Unable to find CoreKeyboard in X configuration; attempting to add new
         CoreKeyboard section.


WARNING: The CoreKeyboard device was not specified explicitly in the layout;
         using the first keyboard device.


ERROR: Unable to write to directory '/etc/X11'.


Please help

---

### Post by Mortuis on 2009-04-26
I'm in the same exact boat.  I was using envy ng to configure nvidia before, but now it's saying that it can't find the kernel headers.  When I check apt for the kernel headers package, there doesn't appear to be one for 2.6.27-7

---

### Post by Refefer on 2009-04-26
I'm having the exact same problem: my 8800GT worked great in 8.10 but now is dumping me into low graphics mode whenever I load up the machine.  Hardware drivers indicate that the nvidia drivers are running whereas nvidia x config is adamant they are not.

Any ideas would be appreciated by many it would appear.

---

### Post by TheLions on 2009-04-26
go here and put those:
[https://launchpad.net/~ubuntu-x-swat/+archive/x-updates](https://launchpad.net/~ubuntu-x-swat/+archive/x-updates)


into your software sources/repository

and just check for new upgrades

or manualy go here:
[https://launchpad.net/~ubuntu-x-swat/+archive/x-updates/+sourcepub/597326/+listing-archive-extra](https://launchpad.net/~ubuntu-x-swat/+archive/x-updates/+sourcepub/597326/+listing-archive-extra)

and download 
[https://launchpad.net/%7Eubuntu-x-swat/+archive/x-updates/+sourcepub/597326/+files/nvidia-180-modaliases_180.53-0ubuntu2_amd64.deb](https://launchpad.net/%7Eubuntu-x-swat/+archive/x-updates/+sourcepub/597326/+files/nvidia-180-modaliases_180.53-0ubuntu2_amd64.deb)
[https://launchpad.net/%7Eubuntu-x-swat/+archive/x-updates/+sourcepub/597326/+files/nvidia-180-kernel-source_180.53-0ubuntu2_amd64.deb](https://launchpad.net/%7Eubuntu-x-swat/+archive/x-updates/+sourcepub/597326/+files/nvidia-180-kernel-source_180.53-0ubuntu2_amd64.deb)
[https://launchpad.net/%7Eubuntu-x-swat/+archive/x-updates/+sourcepub/597326/+files/nvidia-glx-180_180.53-0ubuntu2_amd64.deb](https://launchpad.net/%7Eubuntu-x-swat/+archive/x-updates/+sourcepub/597326/+files/nvidia-glx-180_180.53-0ubuntu2_amd64.deb)
[https://launchpad.net/%7Eubuntu-x-swat/+archive/x-updates/+sourcepub/597326/+files/nvidia-180-libvdpau_180.53-0ubuntu2_amd64.deb](https://launchpad.net/%7Eubuntu-x-swat/+archive/x-updates/+sourcepub/597326/+files/nvidia-180-libvdpau_180.53-0ubuntu2_amd64.deb)

---

### Post by Mortuis on 2009-04-26
An alternative solution which worked for me was switching kernels from 2.6.27-7 to 2.6.28-11, only because headers are available for that kernel. I don't know what other implications there are for switching kernels like that, but I'm not noticing any other problems.

---

### Post by encyd on 2009-04-27
I too experienced this prob - I'm running the -server kernel but the upgrade didn't seem to install the kernel-headers package for my running kernel. I added this in to the package manager, installed it and rebooted and my settings came back perfectly.

HTH someone else.

Cheers,
encyd

---

### Post by Teh H4rRy on 2009-04-28
Im still stuck, The hardware drivers option asks me to install version 96, Surely i want version 180. How do i get version 180?

---

### Post by DenysT on 2009-04-28
> **Teh H4rRy said:**
> Im still stuck, The hardware drivers option asks me to install version 96, Surely i want version 180. How do i get version 180?

I had the same thing happen. I went ahead and installed version 96 and as soon as it finished the updater brought up versions 173 and 180, why it skipped 177 I don't know. But from there I was able to get version 180 working.

---

### Post by Kasese on 2009-04-28
If by chance you have the Hauppauge 1600 TV tuner or similar card, you may want to try adding "vmalloc=256M" to the kernel line in your /boot/grub/menu.lst similar to this:

```
kernel /boot/vmlinuz-2.6.27-11-generic root=UUID=832bbe13-04b6-4cab-b4cc-a2af5fb8d479 ro quiet splash rootflags=data=writeback vmalloc=256M
```


After hours of research, I finally discovered that a well documented conflict between Nvidia drivers and the cx18 drivers were preventing each other from running and need a boost in Ram when loading.

If you don't have the above card, you have a different driver that is interfering with Nvidia. Check the log using 

```
(grep "^(EE)" /var/log/Xorg.0.log
```

Here's thread with more info:

[http://ubuntuforums.org/showthread.php?p=6315676#post6315676](http://ubuntuforums.org/showthread.php?p=6315676#post6315676)

---

### Post by Chaaaaaaaalie on 2009-05-03
When I installed Ubuntu 9.04, the 180 driver was already there under 'Hardware Drivers'  and I just clicked 'Install' and it worked.  

My question is:  Is the Nvidia version 180 the same as 180.51?

---

### Post by TheLions on 2009-05-04
it's little bit older i think it is 180.47.
But if it is working then don't change it!

---

### Post by loxety on 2009-05-05
> **TheLions said:**
> go here and put those:
[https://launchpad.net/~ubuntu-x-swat/+archive/x-updates](https://launchpad.net/~ubuntu-x-swat/+archive/x-updates)


into your software sources/repository

and just check for new upgrades

or manualy go here:
[https://launchpad.net/~ubuntu-x-swat/+archive/x-updates/+sourcepub/597326/+listing-archive-extra](https://launchpad.net/~ubuntu-x-swat/+archive/x-updates/+sourcepub/597326/+listing-archive-extra)

and download 
[https://launchpad.net/%7Eubuntu-x-swat/+archive/x-updates/+sourcepub/597326/+files/nvidia-180-modaliases_180.53-0ubuntu2_amd64.deb](https://launchpad.net/%7Eubuntu-x-swat/+archive/x-updates/+sourcepub/597326/+files/nvidia-180-modaliases_180.53-0ubuntu2_amd64.deb)
[https://launchpad.net/%7Eubuntu-x-swat/+archive/x-updates/+sourcepub/597326/+files/nvidia-180-kernel-source_180.53-0ubuntu2_amd64.deb](https://launchpad.net/%7Eubuntu-x-swat/+archive/x-updates/+sourcepub/597326/+files/nvidia-180-kernel-source_180.53-0ubuntu2_amd64.deb)
[https://launchpad.net/%7Eubuntu-x-swat/+archive/x-updates/+sourcepub/597326/+files/nvidia-glx-180_180.53-0ubuntu2_amd64.deb](https://launchpad.net/%7Eubuntu-x-swat/+archive/x-updates/+sourcepub/597326/+files/nvidia-glx-180_180.53-0ubuntu2_amd64.deb)
[https://launchpad.net/%7Eubuntu-x-swat/+archive/x-updates/+sourcepub/597326/+files/nvidia-180-libvdpau_180.53-0ubuntu2_amd64.deb](https://launchpad.net/%7Eubuntu-x-swat/+archive/x-updates/+sourcepub/597326/+files/nvidia-180-libvdpau_180.53-0ubuntu2_amd64.deb)

Thanks you helped me solve my issue!  Many thanks!  :popcorn:

---

### Post by mrphoenix on 2009-05-06
> **TheLions said:**
> go here and put those:
[https://launchpad.net/~ubuntu-x-swat/+archive/x-updates](https://launchpad.net/~ubuntu-x-swat/+archive/x-updates)


into your software sources/repository

and just check for new upgrades

or manualy go here:
[https://launchpad.net/~ubuntu-x-swat/+archive/x-updates/+sourcepub/597326/+listing-archive-extra](https://launchpad.net/~ubuntu-x-swat/+archive/x-updates/+sourcepub/597326/+listing-archive-extra)

and download 
[https://launchpad.net/%7Eubuntu-x-swat/+archive/x-updates/+sourcepub/597326/+files/nvidia-180-modaliases_180.53-0ubuntu2_amd64.deb](https://launchpad.net/%7Eubuntu-x-swat/+archive/x-updates/+sourcepub/597326/+files/nvidia-180-modaliases_180.53-0ubuntu2_amd64.deb)
[https://launchpad.net/%7Eubuntu-x-swat/+archive/x-updates/+sourcepub/597326/+files/nvidia-180-kernel-source_180.53-0ubuntu2_amd64.deb](https://launchpad.net/%7Eubuntu-x-swat/+archive/x-updates/+sourcepub/597326/+files/nvidia-180-kernel-source_180.53-0ubuntu2_amd64.deb)
[https://launchpad.net/%7Eubuntu-x-swat/+archive/x-updates/+sourcepub/597326/+files/nvidia-glx-180_180.53-0ubuntu2_amd64.deb](https://launchpad.net/%7Eubuntu-x-swat/+archive/x-updates/+sourcepub/597326/+files/nvidia-glx-180_180.53-0ubuntu2_amd64.deb)
[https://launchpad.net/%7Eubuntu-x-swat/+archive/x-updates/+sourcepub/597326/+files/nvidia-180-libvdpau_180.53-0ubuntu2_amd64.deb](https://launchpad.net/%7Eubuntu-x-swat/+archive/x-updates/+sourcepub/597326/+files/nvidia-180-libvdpau_180.53-0ubuntu2_amd64.deb)

Thanks for the help.. but an **IMPORTANT NOTE: before updating NVIDIA driver YOU MUST MAKE A BACKUP FROM THE ORIGINAL (which is workink perfectly now) XORG.CONF FROM YOUR /etc/X11/ DIRECTORY! After updating NVIDIA driver YOU MUST REPLACE YOUR NEW xorg.conf WITH THIS BACKUPPED ONE!**:guitar:

_________________________________________

**[http://phoenix_art.wps4.info/](http://phoenix_art.wps4.info/)**

---

### Post by dreperk on 2009-05-07
I had an issue with the Nvidia drivers on both of my most recent fresh installs of Jaunty.  The restricted drivers were not available via the Restricted Drivers gui.  What I did was make sure (on a fresh install, mind you) that the nvidia drivers and the nvidia-settings gui were both installed.  I ran nvidia-settings (sudo or not, doesn't matter), and it came up with an error message stating that the drivers are not in use.  It gave a simple command to type in terminal to initiate the drivers.  After doing that and restarting X everything worked great.  This was on a Compaq notebook and an Acer notebook.  I can't remember the command because I only had to do it twice, but if you start nvidia-settings from a fresh install it should pop up.

---

### Post by commonplace on 2009-05-08
> **dreperk said:**
> I had an issue with the Nvidia drivers on both of my most recent fresh installs of Jaunty.  The restricted drivers were not available via the Restricted Drivers gui.  What I did was make sure (on a fresh install, mind you) that the nvidia drivers and the nvidia-settings gui were both installed.  I ran nvidia-settings (sudo or not, doesn't matter), and it came up with an error message stating that the drivers are not in use.  It gave a simple command to type in terminal to initiate the drivers.  After doing that and restarting X everything worked great.  This was on a Compaq notebook and an Acer notebook.  I can't remember the command because I only had to do it twice, but if you start nvidia-settings from a fresh install it should pop up.

For everyone's future reference, the command that nvidia-settings prompts you to run is (as sudo/root):

```
nvidia-xconfig
```

I'm going to try it out on my wife's laptop tonight and we'll see what happens! :)

/Kevin

---

### Post by Criminal.Sausage on 2009-05-20
Right, I've got it fixed.

It appears to be a problem with grub. When updating from 8.04 to 9.04 I chose to keep my menu.lst. That is where it went wrong. Here is how to fix it:

```
sudo gedit /boot/grub/menu.lst 
```

Copy the the first option and modify it to look like this (do not replace, as it might give you a fallback option in case it won't work):
**Important, do not copy paste!** it will render your boot useless as your pc has another UUID. Simply modify the bold text. 

```
title Ubuntu 9.04, kernel 2.6.**28-11-**generic
root (hd0,6)
kernel /boot/vmlinuz-2.6.**28-11-**-generic root=UUID=e7910a931-108d-5091-b7b4-1a83a8bad99 ro quiet splash
initrd /boot/initrd.img-2.6.**28-11-**-generic
```

Then execute 
```
sudo grub-install hd0
```

This should do the trick. At least my boot went back to normal again. No nvidia error messages etc. Startup might take a little longer than usual though and don't be scared by the text;-)



P.S.
> For everyone's future reference, the command that nvidia-settings prompts you to run is (as sudo/root):

Code:

nvidia-xconfig

I'm going to try it out on my wife's laptop tonight and we'll see what happens!

/Kevin 
This won't work. It will either give an error or simply do nothing at all. I've tried it multiple times.

---

### Post by commonplace on 2009-05-20
> **Criminal.Sausage said:**
> 

This won't work. It will either give an error or simply do nothing at all. I've tried it multiple times.

Hmm. Well, it worked for me. Not sure what's different with my setup than yours, though. Weird. I don't want to try to break it, though. :)

/Kevin

---

### Post by thelamer on 2009-05-26
> **TheLions said:**
> go here and put those:
[https://launchpad.net/~ubuntu-x-swat/+archive/x-updates](https://launchpad.net/~ubuntu-x-swat/+archive/x-updates)


into your software sources/repository

and just check for new upgrades

or manualy go here:
[https://launchpad.net/~ubuntu-x-swat/+archive/x-updates/+sourcepub/597326/+listing-archive-extra](https://launchpad.net/~ubuntu-x-swat/+archive/x-updates/+sourcepub/597326/+listing-archive-extra)

and download 
[https://launchpad.net/%7Eubuntu-x-swat/+archive/x-updates/+sourcepub/597326/+files/nvidia-180-modaliases_180.53-0ubuntu2_amd64.deb](https://launchpad.net/%7Eubuntu-x-swat/+archive/x-updates/+sourcepub/597326/+files/nvidia-180-modaliases_180.53-0ubuntu2_amd64.deb)
[https://launchpad.net/%7Eubuntu-x-swat/+archive/x-updates/+sourcepub/597326/+files/nvidia-180-kernel-source_180.53-0ubuntu2_amd64.deb](https://launchpad.net/%7Eubuntu-x-swat/+archive/x-updates/+sourcepub/597326/+files/nvidia-180-kernel-source_180.53-0ubuntu2_amd64.deb)
[https://launchpad.net/%7Eubuntu-x-swat/+archive/x-updates/+sourcepub/597326/+files/nvidia-glx-180_180.53-0ubuntu2_amd64.deb](https://launchpad.net/%7Eubuntu-x-swat/+archive/x-updates/+sourcepub/597326/+files/nvidia-glx-180_180.53-0ubuntu2_amd64.deb)
[https://launchpad.net/%7Eubuntu-x-swat/+archive/x-updates/+sourcepub/597326/+files/nvidia-180-libvdpau_180.53-0ubuntu2_amd64.deb](https://launchpad.net/%7Eubuntu-x-swat/+archive/x-updates/+sourcepub/597326/+files/nvidia-180-libvdpau_180.53-0ubuntu2_amd64.deb)

Thank you so much man this worked perfectly, I was almost ready to bail on the server headers and go 64 bit..... 32 bit lives on!!

---

### Post by marshman123 on 2009-05-26
Can somebody help me with my drivers issue. I have a couple screenshots here. Please help. [http://www.rideaucrew.com]("http://www.rideaucrew.com/")

---

### Post by Grandma_DOG on 2009-07-23
My problem was the same, NVidia driver was showing it was enabled but nvidia-setting said it wasn't.

Problem turned out that the new kernel was enabled in grub. Menu.lst was pointing to the old kernel and the new nvidia driver wasn't working with it. So enabled, but crashing.

The grub-update didn't fix the menu.lst, I had to manually update grub's menu.lst and POOF it all worked again.

FYI

---

### Post by Wolfhere on 2009-10-29
Man, you saved my.... This worked great for me. I updated to Nvidia 180 kernel source during the upgrade to 2.6.28.16.21 generic and I could no longer do compiz or use the normal or extra in Visual Effects. I am guessing it was the mod aliases not included in the update. Whew! WOW!!

---

### Post by Wolfhere on 2009-10-29
PS. I am responding to TheLamer post.

---

### Post by erickelrojas on 2009-11-10
easy FAQ
[http://www.elleonplateadodeojosrojos.es/blog/controladores-de-nvidia/](http://www.elleonplateadodeojosrojos.es/blog/controladores-de-nvidia/)

---

