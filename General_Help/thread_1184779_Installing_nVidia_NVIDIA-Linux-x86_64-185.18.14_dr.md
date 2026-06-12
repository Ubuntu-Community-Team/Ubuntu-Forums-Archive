---
title: "Installing nVidia NVIDIA-Linux-x86_64-185.18.14 driver"
date: 2009-06-11
forum: General Help
---

### Post by DeMus on 2009-06-11
Hi,
Both yesterday, running kernel 2.6.28-11, as today after installing 2.6.28-13 I have tried to install the latest nVidia driver.
I used a fairly standard way:
```
ctrl-alt-F1
sudo /etc/init.d/gdm stop
sudo sh NV.....**.**run
```

During installation in which no correct kernel package was found and a new one was compiled, the question about the 32 bits libraries was answered with yes, I get the following notice:

```
Searching for conflicting X files
/usr
```

This hangs at 31%. I can stop the installation with ctrl-c and start the gdm with
```
/etc/init.d/gdm start
```
and everything seems to work again. Nothing happened.

Anyone any idea what is going on when the program hangs, why it is hanging and what I can do about it? Every help is highly appreciated.

---

### Post by gradinaruvasile on 2009-06-11
You should install the driver in runlevel 1.

---

### Post by DeMus on 2009-06-11
> **gradinaruvasile said:**
> You should install the driver in runlevel 1.

Sorry, but that doesn't work. I once did that and nVidia gave me the warning this might be dangerous. I could continue if I wanted but they advised not to.

---

### Post by DeMus on 2009-06-11
> **DeMus said:**
> Sorry, but that doesn't work. I once did that and nVidia gave me the warning this might be dangerous. I could continue if I wanted but they advised not to.

Bump

---

### Post by Arup on 2009-06-12
Did you remove linux restricted modules and linux restricted modules common via --purge? After that also remove any nvidia modaliases, after that make sure xorg.dev and build-essential are installed. Then do a ctrl+alt+F1 and login, do a sudo /etc/init.d/gdm stop, then run the nvidia installer, make sure to select yes for 32 bit compatibility and let nvidia set the xorg. do a sudo reboot command. Always works reliably here.

---

### Post by DeMus on 2009-06-12
> **Arup said:**
> Did you remove linux restricted modules and linux restricted modules common via --purge? After that also remove any nvidia modaliases, after that make sure xorg.dev and build-essential are installed. Then do a ctrl+alt+F1 and login, do a sudo /etc/init.d/gdm stop, then run the nvidia installer, make sure to select yes for 32 bit compatibility and let nvidia set the xorg. do a sudo reboot command. Always works reliably here.

Ok, will try that. Will come back here with the result.
Thanks

---

### Post by Arup on 2009-06-12
> **DeMus said:**
> Ok, will try that. Will come back here with the result.
Thanks

I am sure you have made sure to have un-installed any previous nvidia drivers. Good luck.

---

### Post by DeMus on 2009-06-12
> **Arup said:**
> Did you remove linux restricted modules and linux restricted modules common via --purge? After that also remove any nvidia modaliases, after that make sure xorg.dev and build-essential are installed. Then do a ctrl+alt+F1 and login, do a sudo /etc/init.d/gdm stop, then run the nvidia installer, make sure to select yes for 32 bit compatibility and let nvidia set the xorg. do a sudo reboot command. Always works reliably here.

Can somebody please acknowledge to this? It's not that I do not trust the poster, but looking in Synaptic shows me a lot of restricted modules which seems dangerous to just remove.
When it is safe to remove, should I remove all of them, including the ones for the previous kernel versions?

Please advise.

---

### Post by xOrphenochx on 2009-06-12
> **DeMus said:**
> Can somebody please acknowledge to this? It's not that I do not trust the poster, but looking in Synaptic shows me a lot of restricted modules which seems dangerous to just remove.
When it is safe to remove, should I remove all of them, including the ones for the previous kernel versions?

Please advise.

After some random crashes from Compiz I decided to upgrade to the current version. I did as he said when I was doing it and removed any traces of nvidia. After compiling it everything worked. And by the way, the installer script will detect and remove previously installations if it finds them.

---

### Post by gradinaruvasile on 2009-06-12
> **DeMus said:**
> Sorry, but that doesn't work. I once did that and nVidia gave me the warning this might be dangerous. I could continue if I wanted but they advised not to.
This way u make sure u dont have any modules loaded. 
It worked for me every single time...

---

### Post by DeMus on 2009-06-12
> **xOrphenochx said:**
> After some random crashes from Compiz I decided to upgrade to the current version. I did as he said when I was doing it and removed any traces of nvidia. After compiling it everything worked. And by the way, the installer script will detect and remove previously installations if it finds them.

What are the exact commando's to perform these actions?

---

### Post by DeMus on 2009-06-13
> **DeMus said:**
> What are the exact commando's to perform these actions?

Bump

---

### Post by DeMus on 2009-06-14
> **DeMus said:**
> Bump

Bump again

---

### Post by gradinaruvasile on 2009-06-14
Boot in recovery mode, select root terminal, cd to the installer directory
Run the installer:

./NVwhatever --uninstall

This will remove all nvidia libraries etc.

then

dpkg-reconfigure -phigh xserver-xorg

then the installer again:

./NV...

but this time without the --uninstall

And dont worry about the warning a the start because there are different distributions of linux and ubuntu handles runlevels differently.

Mak sure you answer yes at the last question about editing xorg.conf automatically. 

reboot

---

### Post by DeMus on 2009-06-14
> **gradinaruvasile said:**
> Boot in recovery mode, select root terminal, cd to the installer directory
Run the installer:

./NVwhatever --uninstall

This will remove all nvidia libraries etc.

then

dpkg-reconfigure -phigh xserver-xorg

then the installer again:

./NV...

but this time without the --uninstall

And dont worry about the warning a the start because there are different distributions of linux and ubuntu handles runlevels differently.

Mak sure you answer yes at the last question about editing xorg.conf automatically. 

reboot

I give up:

./NVwhatever --uninstall : "No nVidia driver is installed"

dpkg-reconfigure -phigh xserver-xorg : Made backup of /etc/X11/xorg.conf

./NVwhatever : Installation starts with message about runlevel 1, Ok I agree and continue. I accept the license, program is looking for precompiled kernel module, can not find it, will look on the net - can't find it (never can't find it), compiles itself. I say yes to install 32 bit libraries and then it is looking for conflicting X files. At 31% the program hangs. I keep it hanging for a long time but nothing, except some network traffic (lights on external switch are flashing) happens.
After reboot I miss my proprietary driver which I can install and reboot again. Back at square 1.

Any other ideas? Or should I just quit?

---

### Post by kg87 on 2009-06-14
Hey, Im not sure this will help, but check out an app called envy at

[http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)

It worked for me, its all automated. 

however, Im not sure if its an issue with my gfx card, but configuration doesn't seem to work 100% of the time...

---

### Post by DeMus on 2009-06-14
> **kg87 said:**
> Hey, Im not sure this will help, but check out an app called envy at

[http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)

It worked for me, its all automated. 

however, Im not sure if its an issue with my gfx card, but configuration doesn't seem to work 100% of the time...

Yes, I know Envy but it does not show the driver I want to use, only the one I have installed (which is recommended by the program)
Thanks anyway.

---

### Post by kg87 on 2009-06-14
ahh ok no problem, Though it could be worse, you could be usin windows :P

---

### Post by DeMus on 2009-06-14
> **kg87 said:**
> ahh ok no problem, Though it could be worse, you could be usin windows :P

Well, although I am no fan of Windows, installing a new driver is a piece of cake. Why it has to be so difficult in Linux I still don't know.
Thanks for your help.

---

### Post by gradinaruvasile on 2009-06-14
Ok...
I too tried that driver on a 13 kernel (32 bit) and i got black screen (installed ok though)... Had to revert to 11 kernel.
Maybe there is a conflict with the new kernel in this driver?

There is a ppa with this driver

[https://launchpad.net/~thefirstm/+archive/ppa]("https://launchpad.net/~thefirstm/+archive/ppa")

Try it out. U will have to install the 180 drivers but those are really the 185...

---

### Post by DeMus on 2009-06-14
> **gradinaruvasile said:**
> Ok...
I too tried that driver on a 13 kernel (32 bit) and i got black screen (installed ok though)... Had to revert to 11 kernel.
Maybe there is a conflict with the new kernel in this driver?

There is a ppa with this driver

[https://launchpad.net/~thefirstm/+archive/ppa]("https://launchpad.net/~thefirstm/+archive/ppa")

Try it out. U will have to install the 180 drivers but those are really the 185...

Thank you for pointing out the PPA website but I think I will stick to 180.44 for a while, until the new driver is in Synaptic.

---

### Post by gradinaruvasile on 2009-06-14
> **DeMus said:**
> Thank you for pointing out the PPA website but I think I will stick to 180.44 for a while, until the new driver is in Synaptic.

If u install the repo you will install the driver directly from synaptic.

---

### Post by DeMus on 2009-06-14
> **gradinaruvasile said:**
> If u install the repo you will install the driver directly from synaptic.

Okay, I thought: what the hell. If it destroys everything I will re-install Jaunty. I added the repo and upgraded my drivers. It all works. Thank you so much for your help.

---

### Post by gradinaruvasile on 2009-06-14
You are welcome.

---

### Post by mattwilkes512 on 2009-06-23
Is the 185.18.14 driver stable?  I just returned a PNY 8400gs PCI card because none of the drivers (180 and below) in Jockey worked with a fresh install of ubuntu 9.04 on my computer.  I guess this card would have worked with the 185.18.14 driver?  Once you install the PPA in software sources and get the GPG key thingy what files do I install/uninstall though synaptic to get 185.18.14 driver running?  Thanks so much.  I'm totally new to ubuntu and would appriciate your help resurrecting my old dell dimension 2400 !

---

### Post by DeMus on 2009-06-23
> **mattwilkes512 said:**
> Is the 185.18.14 driver stable?  I just returned a PNY 8400gs PCI card because none of the drivers (180 and below) in Jockey worked with a fresh install of ubuntu 9.04 on my computer.  I guess this card would have worked with the 185.18.14 driver?  Once you install the PPA in software sources and get the GPG key thingy what files do I install/uninstall though synaptic to get 185.18.14 driver running?  Thanks so much.  I'm totally new to ubuntu and would appriciate your help resurrecting my old dell dimension 2400 !

I have the files installed as can be seen in the attachement.
In the left column you can see they originate from ppa.launchpad.net/restricted.
The driver is very stable, I have no problem with it what so ever.

---

### Post by mattwilkes512 on 2009-06-23
WOW! Thanks.  That seems like it will be very helpful.  So all you did was install those files and BAM! it worked?  I guess I will order the 8400gs 512mb PNY PCI card again and see if it works.  Stay tuned...

---

