---
title: "screen resolution has gone chunky"
date: 2007-07-25
forum: Desktop Environments
---

### Post by howardde on 2007-07-25
Hi
I booted my pc this morning and the screen resolution has changed. Now everything is chunky, and looking in kde>system settings>monitor and display is not helping. The drag-along bar there won't move, even in admin mode, and is already saying I am on the max resolution.

I am using kubuntu feisty and a philips 170C. I have searched for ages through threads and google, but can't figure out a solution. I downloaded 915 resolution, but don't know if thats actually what i need, or how to use it! ;)

Can anyone help please?
Thanks in advance
Howard

---

### Post by Soybean on 2007-07-25
What sort of video card do you have?

Did you do anything unusual yesterday that might have changed your settings in ways you weren't expecting?

---

### Post by wjp.reg on 2007-07-25
> I downloaded 915 resolution, but don't know if thats actually what i need, or how to use it! 

"915resolution is a tool to modify the video BIOS of the 800
and 900 series Intel graphics chipsets. This includes the 845G,
855G, and 865G chipsets, as well as 915G, 915GM, and 945G chipsets.
This modification is necessary to allow the display of certain
graphics resolutions for an Xorg or XFree86 graphics server."

What video card are you running?

If you don't know, run this in a terminal window:

```
lspci | grep "Graphics"
``` and note the output.

Do you have updates configured to automatically download and install?

Sounds like an update may have messed with your previous video setup.

You could try the following:

Press Alt-F1 and logon; then enter the following:

```
sudo dpkg-reconfigure xserver-xorg
``` You'll be asked to confirm a series of settings.
Select your video driver and supported resolutions when they come up. 

If you have  ATI or nVida video then you will have to reinstall the driver.  Search the forum for further instructions.

Good Luck!

---

### Post by howardde on 2007-07-25
What sort of video card do you have?

Did you do anything unusual yesterday that might have changed your settings in ways you weren't expecting?

Hi,
No card installed. Two things, but neither can really be affecting it. I managed to get my windows box working again, next to this pc, but that is airwalled, and my graphics card arrived in the post, but its in its box!

I've tried sudo dpkg.. but to no immediate effect. Does that need a reboot to work?
I did the usual sudo apt-get update/upgrade this morning, but the screen res thing had already happened, it was chunky on the graphical login.

lspci | grep "Graphics"
 
...just returns me to the command line. I'm pretty sure it is integrated intel, as I've had to reinstall dapper on another partition to fix an xorg/blender problem caused by integrated intel graphics chips. 

The pc is still working so would I be better off installing the nvidia card I just ordered and going from there do you think? Or should i sort the resolution problem out then install the card?

Thanks for your help! :)

---

### Post by wjp.reg on 2007-07-25
I guess it's entirely up to you, whether you install an nvida card first.  If you are definitely going to change video, then you might as well do that first before continuing with the trouble-shooting.

"lspci" on it's own should list all the components in your system and you can eye-ball for anything that suggests to be your video bios brand.

here's my output from "lspci | grep "Graphics"

```
wolf@ubuntu:~$ lspci | grep "Graphics"
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GM/GMS/940GML Express Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/940GML Express Integrated Graphics Controller (rev 03)

```

---

