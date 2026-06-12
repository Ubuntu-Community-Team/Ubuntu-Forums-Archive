---
title: "Dell XPS 15 battery life"
date: 2011-11-19
forum: Dell Ubuntu Support (CLOSED)
---

### Post by Meikrekel on 2011-11-19
Hey all,

I have the following laptop:
Dell XPS 15
Videocard: GT540m 2gb
Processor: i7 2630qm
RAM: 6gb

I've just installed 11.10. After that my battery life was about 2 hours, slightly less. After that I've done the following two things which should've increased my battery life:
- Installed bumblebee (it seems to work because if I run optirun glxgears the gears show up)
- Added GRUB_CMDLINE_LINUX_DEFAULT="quiet splash pcie_aspm=force i915.i915_enable_rc6=1" in /etc/default/grub

After that my battery life should've increased drastically to ~ 6 hours, but it still only is around 2 hours..

Kind regards,
Meikrekel

---

### Post by SavageCHRIS on 2011-11-19
> **Meikrekel said:**
> Hey all,

I have the following laptop:
Dell XPS 15
Videocard: GT540m 2gb
Processor: i7 2630qm
RAM: 6gb

I've just installed 11.10. After that my battery life was about 2 hours, slightly less. After that I've done the following two things which should've increased my battery life:
- Installed bumblebee (it seems to work because if I run optirun glxgears the gears show up)
- Added GRUB_CMDLINE_LINUX_DEFAULT="quiet splash pcie_aspm=force i915.i915_enable_rc6=1" in /etc/default/grub

After that my battery life should've increased drastically to ~ 6 hours, but it still only is around 2 hours..

Kind regards,
Meikrekel

From the information you have gave, it looks like you haven't set up bumblebee to manage your card.

Have you created a 'cardoff' and 'cardon' file with the correct calls for your Nvidia card ?

---

### Post by Meikrekel on 2011-11-20
No I haven't done that, the instructions I followed didn't say that I had to do that. Can you tell me how to do that?

---

### Post by SavageCHRIS on 2011-11-20
By following the guide on this site I have got mine working with 6-7 hours battery life.

[http://www.ivegotavirus.com/blog/2011/11/06/how-to-get-optimus-working-on-ubuntu-11-10-oneiric/](http://www.ivegotavirus.com/blog/2011/11/06/how-to-get-optimus-working-on-ubuntu-11-10-oneiric/)

I have exactly the same laptop as you so it should work fine.

---

### Post by Meikrekel on 2011-11-20
I've followed the instructions on that site, but my battery life is still only around the 2 hours :confused:

EDIT:

The output of 
watch grep rate /proc/acpi/battery/BAT0/state

did change from ~3750 to ~2500 mA

---

### Post by Epinephrin3 on 2011-11-21
Can you post the output of this command to see if your card is being turned off
 
```
lspci -d 10de: -vvnn
```Also did you try the Intel commands?

---

### Post by Meikrekel on 2011-11-22
I did try the intel commands. 

Here is the output of the command you suggested:

```
wouter@Wouter-ubuntu:~$ lspci -d 10de: -vvnn
01:00.0 VGA compatible controller [0300]: nVidia Corporation GF106 [GeForce GT 555M] [10de:0df4] (rev a1) (prog-if 00 [VGA controller])
    Subsystem: Dell Device [1028:050e]
    Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 0, Cache Line Size: 64 bytes
    Interrupt: pin A routed to IRQ 16
    Region 0: Memory at f0000000 (32-bit, non-prefetchable) [size=16M]
    Region 1: Memory at c0000000 (64-bit, prefetchable) [size=256M]
    Region 3: Memory at d0000000 (64-bit, prefetchable) [size=32M]
    Region 5: I/O ports at 3000 [size=128]
    Expansion ROM at f1000000 [disabled] [size=512K]
    Capabilities: <access denied>
    Kernel driver in use: nouveau
    Kernel modules: nvidia_current, nouveau, nvidiafb

wouter@Wouter-ubuntu:~$ 

```

---

### Post by SavageCHRIS on 2011-11-22
> **Meikrekel said:**
> I did try the intel commands. 

Here is the output of the command you suggested:

```
wouter@Wouter-ubuntu:~$ lspci -d 10de: -vvnn
01:00.0 VGA compatible controller [0300]: nVidia Corporation GF106 [GeForce GT 555M] [10de:0df4] (rev a1) (prog-if 00 [VGA controller])
    Subsystem: Dell Device [1028:050e]
    Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 0, Cache Line Size: 64 bytes
    Interrupt: pin A routed to IRQ 16
    Region 0: Memory at f0000000 (32-bit, non-prefetchable) [size=16M]
    Region 1: Memory at c0000000 (64-bit, prefetchable) [size=256M]
    Region 3: Memory at d0000000 (64-bit, prefetchable) [size=32M]
    Region 5: I/O ports at 3000 [size=128]
    Expansion ROM at f1000000 [disabled] [size=512K]
    Capabilities: <access denied>
    Kernel driver in use: nouveau
    Kernel modules: nvidia_current, nouveau, nvidiafb

wouter@Wouter-ubuntu:~$ 

```

Your power usage has gone down because of the intel commands but your Nvidia card is still on, this is because you are using the nouveau driver when you should be using the Nvidia.
 
Try completely removing bumblebee then reinstalling using that guide, also if you have the restricted Nvidia drivers remove them.

If I was you I would just do a full reinstall of Ubuntu as completely removing bumblebee is a pain in the ***, if this isn't an option try what I said but if you run into any problems its probably because bumblebee never uninstalled properly.

---

### Post by Meikrekel on 2011-11-23
That's strange, here's what I did:

- reinstalled ubuntu 11.10
- update all programs
- followed your tutorial

I haven't installed that driver? And because of that a reinstall would be.. strange(?), because the same thing would just happen again I guess

---

### Post by Epinephrin3 on 2011-11-23
When the option appeared to activate the restricted Nvidia drivers (usually the first time u log in after a new install) did you choose to active them?

Also you did say in your original post;
> I've just installed 11.10. After that my battery life was about 2 hours,  slightly less. After that I've done the following two things which  should've increased my battery life:
- Installed bumblebee (it seems to work because if I run optirun glxgears the gears show up)
- Added GRUB_CMDLINE_LINUX_DEFAULT="quiet splash pcie_aspm=force i915.i915_enable_rc6=1" in /etc/default/grub

So it sounds like you had already install Bumblebee before you followed the tutorial on ivegotavirus.com ?

---

### Post by Meikrekel on 2011-11-23
After that you posted that tutorial, I did a full uninstall and install. After that I did an upgrade to make sure I was totally up to date and after that I followed your tutorial

Thanks for your help!

---

### Post by Epinephrin3 on 2011-11-23
Ok now I understand...

Open up your xorg.conf.nvidia
```
sudo gedit /etc/bumblebee/xorg.conf.nvidia
```Search for 'Driver' and it should say Nvidia. If it says Nouveau change it to look like this
```
Driver "nvidia"
```Save then restart.

---

### Post by Meikrekel on 2011-11-25
I have checked your solution, but the driver already says nvidia and not nouveau. Strange

---

### Post by Epinephrin3 on 2011-11-25
You can remove your Nouveau drivers and bumblebee will then only be able  to use your Nvidia drivers and not get confused by having both  installed. I have done this myself and i also know another user who has  done exactly the same without any problems but there always might be a  risk of not being able to boot back into your install as with anything  when you play around with your display drivers. But its up to you though  bud and like i said the same has worked for me and other users.

To remove it in the terminal type:
```
sudo apt-get remove xserver-xorg-video-nouveau
```

---

### Post by Epinephrin3 on 2011-11-27
It looks like the issue has been found. one of our user noticed that if you completely disable the Nouveau drivers and kernel module it resolves the problem. You can find out how here: [https://wiki.ubuntu.com/X/Troubleshooting/Nouveau#Disabling_nouveau](https://wiki.ubuntu.com/X/Troubleshooting/Nouveau#Disabling_nouveau)

---

### Post by Caluca on 2012-01-11
Hello there,

I am experiencing the same problems. My battery life is just a little over 2 hours. I have the following laptop (for about 3 weeks now):

Dell XPS 15 L502X
CPU : 2nd generation Core i7 - 2670QM
GPU : GeForce GT 540M 2GB
RAM : 8192 MB
HDD : 750 GB SerialATA 7200 RPM
DISP: 15.6 inch FHD B+RGLED True-Life 1920x1080
BAT : 6 cell 56W
WiFi: Intel Centrino Wireless-N 1030

I am running on Kubuntu 11.10 (NOT UBUNTU 11.10).



=======================
What have I done so far
=======================

- Install Kubuntu 11.10
- Install Synaptics
- Run updates with Synaptics, reboot
- Run Jockey, select recommended Nvidia drivers, reboot
- Apparently also installed noveau drivers (do not know when)
- Disabled Akonadi and Nepomuk (Personal Information Managers)
- Disabled noveau with:

```
echo options nouveau noaccel=1 | sudo tee -a /etc/modprobe.d/nouveau-kms.conf
sudo update-initramfs -u
```
  
  As explained in:
  [https://wiki.ubuntu.com/X/Troubleshooting/Nouveau#Disabling_nouveau]("https://wiki.ubuntu.com/X/Troubleshooting/Nouveau#Disabling_nouveau")



===================
What haven´t I done
===================

- Install Bumblebee



===============
Current outputs
===============

```
lspci -d 10de: -vvnn
```

```
01:00.0 VGA compatible controller [0300]: nVidia Corporation GF106 [GeForce GT 555M] [10de:0df4] (rev a1) (prog-if 00 [VGA controller])
        Subsystem: Dell Device [1028:050e]
        Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
        Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
        Latency: 0, Cache Line Size: 64 bytes
        Interrupt: pin A routed to IRQ 16
        Region 0: Memory at f0000000 (32-bit, non-prefetchable) [size=16M]
        Region 1: Memory at c0000000 (64-bit, prefetchable) [size=256M]
        Region 3: Memory at d0000000 (64-bit, prefetchable) [size=32M]
        Region 5: I/O ports at 3000 [size=128]
        Expansion ROM at f1000000 [disabled] [size=512K]
        Capabilities: <access denied>
        Kernel driver in use: nvidia
        Kernel modules: nvidia_current, nouveau, nvidiafb
```


```
glxinfo
```

```
Xlib:  extension "GLX" missing on display ":0".
Xlib:  extension "GLX" missing on display ":0".
Xlib:  extension "GLX" missing on display ":0".
Xlib:  extension "GLX" missing on display ":0".
Xlib:  extension "GLX" missing on display ":0".
Error: couldn't find RGB GLX visual or fbconfig                                                                                                                                                                                                                                
                                                                                                                                                                                                                                                                               
Xlib:  extension "GLX" missing on display ":0".                                                                                                                                                                                                                                
Xlib:  extension "GLX" missing on display ":0".                                                                                                                                                                                                                                
Xlib:  extension "GLX" missing on display ":0".                                                                                                                                                                                                                                
Xlib:  extension "GLX" missing on display ":0".                                                                                                                                                                                                                                
Xlib:  extension "GLX" missing on display ":0".                                                                                                                                                                                                                                
Xlib:  extension "GLX" missing on display ":0".                                                                                                                                                                                                                                
Xlib:  extension "GLX" missing on display ":0".
```

```
grep rate /proc/acpi/battery/BAT0/state
```

```
present rate:            2417 mA
```



=========================
What do I want to achieve
=========================

- At least 4 hours of battery life on Kubuntu 11.10



======================
What do I want to know
======================

- Does the Bumblee tutorial in this thread also work for Kubuntu?
- How can I check whether I have restricted drivers?


**NOTE: **Even though I ´removed´ noveau with the commands in the link posted in the previous post, it is still present in:

```
lspci -d 10de: -vvnn
```
**NOTE: **Directly after removing noveau and rebooting my power level dropped to ~750 mA. I left my laptop for dinner. Afterwards I entered my screen saver password and checked the power level again. It was now back to ~2500 mA. Rebooting did not help.

I thank you all for your time and effort!

---

### Post by Caluca on 2012-01-11
I have installed Optimus anyways. It is working fine (it did not give me any errors). My power level has decreased from ~2400 to ~1100. So that is looking good. I however do not know whether it was due to the Intel commands or Optimus. Unfortunately my battery indicator is not working that well. I can only see percentages and no times. So I have to time a full discharge.

I ran this command:

```
lspci -d 10de: -vvnn
```

and got

```
01:00.0 VGA compatible controller [0300]: nVidia Corporation GF106 [GeForce GT 555M] [10de:0df4] (rev ff) (prog-if ff)
        !!! Unknown header type 7f
```

Is this okay, or is something seriously wrong?

Finally how can I verify whether Optimus is really working, whether it is managing my GPU or not?

---

### Post by Epinephrin3 on 2012-01-14
> **Caluca said:**
> I have installed Optimus anyways. It is working fine (it did not give me any errors). My power level has decreased from ~2400 to ~1100. So that is looking good. I however do not know whether it was due to the Intel commands or Optimus. Unfortunately my battery indicator is not working that well. I can only see percentages and no times. So I have to time a full discharge.

I ran this command:

```
lspci -d 10de: -vvnn
```and got

```
01:00.0 VGA compatible controller [0300]: nVidia Corporation GF106 [GeForce GT 555M] [10de:0df4] (rev ff) (prog-if ff)
        !!! Unknown header type 7f
```Is this okay, or is something seriously wrong?

Finally how can I verify whether Optimus is really working, whether it is managing my GPU or not?

 Well it looks like you done a good job at getting it setup. '!!! Unknown header type 7f' means that your card is off. you will be seeing a big drop in battery usage with it being disabled. 

If you run a program with the optimus command for example 'optimus firefox' it should switch your nvidia chip back on and use it for that program. when you close firefox it will turn off the nvidia chip again and save power.

---

### Post by Caluca on 2012-01-17
Thanks. I thought I had done something really bad. Unfortunately I f'd OS afterwards. Whenever I rebooted my system, the only thing I could do was log-in and then everything became black. Not one button or shortcut worked. This is however not related to Optimus, but just me being stupid and a linux-n00b.

I formatted my entire drive and reinstalled Windows 7 (yes I am dual-booting). Still need to install Kubuntu. Probably doing that tonight.

Thanks for your help!

---

### Post by Caluca on 2012-01-30
One last question. You said your battery lasts for about six hours. But do you have the 6 or 9 cell battery? Cause mine is giving me just 4 hours and I have a 6 cell. So I am guessing that you have a 9 cell, correct?

---

### Post by Meikrekel on 2012-03-29
I've managed to get bumblebee working on Ubuntu 11.10 and have been using Ubuntu as my main OS ever since (I think I'm using it now for a month).

I'd like to upgrade to 12.04 beta 2 now, but I think this will break bumblebee.. So the question is: will upgrading to 12.04 break my bumblebee setup?

---

