---
title: "Ubuntu no longer able to boot"
date: 2008-12-10
forum: General Help
---

### Post by Talan6400 on 2008-12-10
Ok I looked through the threads and could find anything that matches my issue exactly so I need to start one to ask.  Sorry if this has already been addressed and I just didn't find it.

1. I am still a noob so forgive me if (when) I sound stupid.

Issue:

After upgrading my system from 8.04 to 8.10, I experienced a system lock up and had to hard boot the machine.  After this I am no longer able to boot to my Ubuntu drive. Grub seems to work as the menu will come up ok and let me boot to my XP drive.  When I attempt to boot to Ubuntu, I will get the splash screen, then it goes into what looks to be repair mode, and I get a continuous list of errors scrolling on the screen.  I let this go overnight once and in the morning (8hrs later) it was still scrolling errors.  I can post errors if needed but not at home to get error right now.

What I am looking for is advice on my next steps to attempt to repair.  I have used a live disk to boot to and copied my pictures music docs ect over to a folder on my windows drive, so I will not be losing anything important if it comes to a complete reinstall, just alot of time and tweaking of my desktop/system.

I have not attempted reloading Grub as I am not convinced that is the issue, although if that is a good starting place I will attempt.

I also have seen information about reinstalling into a different partition so that the home directory information can be copied over when complete so as to not lose that data. 

I know I made a huge mistake when I installed 8.04 the first time, by only creating one large partition and not seperate for OS and home directories, so I'm not sure if I will actually be able to rescue my data.

I am also wondering if I can use the live cd to boot to and then mount Linux disk and run an fsck to "hopefully" repair issues.

Any help/suggestions will be greatly appreciated

---

### Post by taurus on 2008-12-10
You can run fsck from a terminal of your Ubuntu partition from the LiveCD to see if it fixes whatever the problem that you have experienced.

```
fsck /dev/sda2
```
Assuming /dev/sda2 is the partition where you installed Ubuntu on.  If not sure, look at the output of this command from a terminal.

```
sudo fdisk -l
```

---

### Post by sayakb on 2008-12-10
Can you boot into the "Recovery mode" from GRUB?
If so, try this command:
```
sudo apt-get update && sudo apt-get upgade
```
If it shows "Broken packages", do:
```
sudo apt-get install -f
```

You may have unconfigured but installed files. To configure them, do:
```
sudo dpkg-reconfigure -a
```

---

### Post by Talan6400 on 2008-12-10
No I can't boot into the recovery mode from grub, when I attempted to I got the same scrolling error messages I get after splash screen when trying to boot normal.

Thanks.

---

### Post by Talan6400 on 2008-12-10
Will try as soon as I get up this afternoon (am working night shift right now and away from that system).

---

### Post by sayakb on 2008-12-10
In that case, I would then suggest a clean install. At the LiveCD menu, choose "Try ubuntu without making changes..." option and copy all content of your /home to a safe place.

---

### Post by eternalnewbee on 2008-12-10
**Originally posted by LinuxIsInnovation**
```
sudo apt-get update && sudo apt-get upgade
```
You mean upgrade:p

---

### Post by TeXtonyx on 2008-12-10
I'm wondering what caused the problem. Support for some nVidia
and Ati video cards suffered some attrition. Do you think it could 
be a driver run amok? Have a more ordinary card. Just an idea.

---

### Post by Talan6400 on 2008-12-10
I'm using nVidia 7950GT.  Using recommended driver in 8.04, with no issues.  After upgrading it dod boot and start X once but locked up and wouldn't let me open/run/click on anything.  After hard booting it wouldn't boot successfully again.  

Does that sound like it could be the video driver?

Could the hard boot have messed up the driver?

But why the errors even when trying to go to recover mode?

Just kicking things around, am listening to everything right now.:p

---

### Post by TeXtonyx on 2008-12-10
> **Talan6400 said:**
> I'm using nVidia 7950GT.  Using recommended driver in 8.04, with no issues.  After upgrading it dod boot and start X once but locked up and wouldn't let me open/run/click on anything.  After hard booting it wouldn't boot successfully again.  

Does that sound like it could be the video driver?

Could the hard boot have messed up the driver?

But why the errors even when trying to go to recover mode?

Just kicking things around, am listening to everything right now.:p

TeX replied, requoting myself:

From the 8.10 Release Notes:

nVidia "legacy" video support

"The 71 and 96 series of proprietary nVidia drivers, as provided 
by the nvidia-glx-legacy and nvidia-glx packages in Ubuntu 8.04 
LTS, are not compatible with the X.Org included in Ubuntu 8.10. 

Users with the nVidia TNT, TNT2, TNT Ultra, GeForce, GeForce2, 
GeForce3, and GeForce4 chipsets are affected and will be 
transitioned on upgrade to the free nv driver instead. This 
driver does not support 3D acceleration. 

Users of other nVidia chipsets that are supported by the 173 or 
177 driver series will be transitioned to the nvidia-glx-173 or 
nvidia-glx-177 package instead. However, unlike drivers 96 and 
71, drivers 173 and 177 are only compatible with CPUs that 
support SSE (e.g. Intel Pentium III, AMD Athlon XP or higher). 
Systems with older CPUs will also be transitioned to the nv 
driver on upgrade."

TeX:
SSE = Athlon XP processor or newer and I think Pentium III 
check your motherboard manual if in doubt. Also there are a
lot of Howtos written for the Nvidia driver and particular
Nvidia cards which you can find in the Ubuntu Search window.

[http://ubuntuforums.org/showthread.php?t=1000442&highlight=7950GT](http://ubuntuforums.org/showthread.php?t=1000442&highlight=7950GT)
SeePU has your card and video problems with Intrepid/Kubuntu 
that uses KDE rather than Gnome. 

No I don't think the hard boot damaged the driver, more likely
you had to hard boot because that correct driver wasn't installed.
But you could have other issues going on, besides the driver.

My idea is that since 8.10 isn't working, why not reinstall it
in text mode which uses an ordinary driver. You will get low
resolution, but if you boot a few times and there is no other
error message, it is likely safe to assume it was just a driver
problem. If you do get non-driver or X related error messages
write them down. 

Well, if it works after the text mode reinstall, (delete the 8.10
partitions first), then you can upgrade to the proper driver. The 
nVidia drivers are not always easy to install, I had some luck with 
Envyng I think it was called. Text mode is an "alternate cd" option.

---

