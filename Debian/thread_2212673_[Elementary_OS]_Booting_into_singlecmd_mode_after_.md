---
title: "[Elementary OS] Booting into singlecmd mode after hda-intel error"
date: 2014-03-22
forum: Debian
---

### Post by brent_berghmans2 on 2014-03-22
[COLOR=#000000][FONT=verdana]Hey guys!
[/FONT][/COLOR]
[COLOR=#000000][FONT=verdana]I decided to try out Elementary OS a couple of months ago, so I made a live USB stick, 
installed it alongside windows 8 (on UEFI hardware) succesfully, but when I booted it I got this error: 
[I]&#8220;hda-intel: azx_get_response timeout switching to singlecmd mode&#8221;
[/I] At the time I hadn't really used Linux before so I had no clue on what it meant or what to do.
[/FONT][/COLOR]
[COLOR=#000000][FONT=verdana]So I tried other distro's, I tried crunchbang and debian first. Neither one of them worked. I tried others aswell (Fedora, Ubuntu, Linux Mint), 
they did work **after** I added *"acpi_osi=Linux acpi_backlight=vendor nouveau.modeset=0"* to the grub startup code.
[/FONT][/COLOR]
[COLOR=#000000][FONT=verdana]I used Linux Mint for a long time but I still wanted try Elementary OS. And since I had more experience with Linux I thought I would be able to get it to work this time. I have proven myself wrong[/FONT][/COLOR]
[COLOR=#000000][FONT=verdana]I made a live usb of Elementary OS, plugged it in, added *"acpi_osi=Linux acpi_backlight=vendor nouveau.modeset=0"* to the grub startup code this time and booted it. 
I got the **same** result: *&#8220;hda-intel: azx_get_response timeout switching to singlecmd mode&#8221;*[/FONT][/COLOR]
[COLOR=#000000][FONT=verdana]
[/FONT][/COLOR]Is there any way to fix this issue? 
[COLOR=#000000][FONT=verdana]Any help would be much appriciated. :)
[/FONT][/COLOR]



TLDR: I get the error *&#8220;hda-intel: azx_get_response timeout switching to singlecmd mode&#8221; everytime *on boot and I can't get to the desktop, it just stays at the command line.


[LIST]
[*]Program I used to make a bootable usb: Universal USB Installer
[*]CPU: i7-4702MQ
[*]GPU: Geforce GT750M
[*]Windows 8 64-Bit UEFI Firmware
[*]Laptop: Acer V3-772G
[/LIST]

---

### Post by Stinger on 2014-03-22
Welcome to the Ubuntu forums.

Did you try the nomodeset kernel option from the live media ? there a nice thread about  [How to set NOMODESET and other kernel boot options in grub2]("http://ubuntuforums.org/showthread.php?t=1613132&p=10069997#post10069997"), scroll down to where it says [COLOR="#FF0000"]'How to enable kernel options on the livecd (before install)'[/COLOR] . I know it's a bit old but I think it's still valid. See if that helps you.

It's quite new hardware you've got, maybe you'll need a newer kernel and X-server too ( elementary is based on Precise, Ubuntu 12,04 ) _but don't do it unless you really need it, it can do more damage than joy !_
[LTS Enablement Stacks ]("https://wiki.ubuntu.com/Kernel/LTSEnablementStack")

---

### Post by brent_berghmans2 on 2014-03-22
I tried with boot options : "acpi_osi=Linux acpi_backlight=vendor quiet splash nomodeset" but it resulted in the same error :/
I also tried "startx" in the singlecmd mode and it said : "fatal error: no screens found".

I will try updating the kernel and xserver but I'm a bit worried by** "**[U]but don't do it unless you really need it, it can do more damage than joy"
[/U]What are the risks etc?

Thanks for the reply btw :)

---

### Post by Stinger on 2014-03-23
What does booting with only the nomodeset option from the live media give you ? ( described in the link I gave you )

Also try this from the command line to see what graphics you are using :
```
lspci | grep VGA & sudo lshw -C video
```
Remember to type in your password when asked for

Here is my output for comparison :
> [1] 8946
01:00.0 VGA compatible controller: Advanced Micro Devices, Inc. [AMD/ATI] RV730 XT [Radeon HD 4670]
[sudo] password for xxxx: 
  *-display               
       description: VGA compatible controller
       product: RV730 XT [Radeon HD 4670]
       vendor: Hynix Semiconductor (Hyundai Electronics)
       physical id: 0
       bus info: pci@0000:01:00.0
       version: 00
       width: 64 bits
       clock: 33MHz
       capabilities: pm pciexpress msi vga_controller bus_master cap_list rom
       configuration: driver=radeon latency=0
       resources: irq:44 memory:d0000000-dfffffff memory:fe9f0000-fe9fffff ioport:c000(size=256) memory:fe9c0000-fe9dffff
[1]+  Done                    lspci | grep --color=auto VGA

I lost my wireless network when using the LTS Enablement stacs, no joy for me, had to revert to the original kernel and x-server, should only be used as a last resort when you are running out of options.

---

### Post by brent_berghmans2 on 2014-03-23
Alright, this is with only nomodeset, and I ran the command you asked for. :)
Also I don't know if it matters but as you see, I have 2 'graphic cards', the integrated intel one and the nvidia one.
When I was using Linux Mint it only detected my integrated intel one. When I tried to install nvidia drivers my screen would not work, it was just black.

[ATTACH=CONFIG]251400[/ATTACH]

---

### Post by Stinger on 2014-03-23
It matters
Thats your problem in a nutshell :)
It seems that elementary ( or Precise ) would like to use your Nvidia card  ( physical id: 0 ) but the X-server can't cope with it ( maybe to old )

I don't like the two lines:
> *-display UNCLAIMED
and
> configuration: latency=0
The driver bit is missing if you compare with my output.

Did you by any chance try the Ubuntu 14.04 development release, live version will do ? Just to see if a newer kernel and x-server solves the problem before using the LTS enablement stack.

BTW. When you used elementary as a live media, before installing, you had graphics, right ? 
It's only when installed you lose the graphics ?

---

### Post by Stinger on 2014-03-23
If you install the mesa-utils package :
```
sudo apt-get install mesa-utils
```
You can try running :
```
glxinfo | grep render
```

Here is my output:
> direct rendering: Yes
OpenGL renderer string: Gallium 0.4 on AMD RV730
    GL_EXT_vertex_array_bgra, GL_NV_conditional_render, 

---

### Post by brent_berghmans2 on 2014-03-23
No, the live media does not work either (I didn't test it before installing, yeah that was dumb), funny enough though the graphical installer does work and shows the background of elementary etc. 
(In short 'Try elementary without installing' does not work but 'Install elementary' works correctly and shows a desktop)
I think I also tried to install the bumblebee drivers on Linux which also didn't work if you were wondering :p

I will try Ubuntu 14.04 and the command you asked later this day and I will post the result. :)

---

### Post by brent_berghmans2 on 2014-03-23
Ok so I made a live boot of ubuntu 14.04 and to my suprise it worked out of the box.
I didnt even have to add:
```
acpi_osi=Linux acpi_backlight=vendor
```

Which I had to do in other distros or I would have no display.

Also here is the lspci info:
```
[1] 3687
00:02.0 VGA compatible controller: Intel Corporation 4th Gen Core Processor Integrated Graphics Controller (rev 06)
  *-display               
       description: 3D controller
       product: GK107M [GeForce GT 750M]
       vendor: NVIDIA Corporation
       physical id: 0
       bus info: pci@0000:01:00.0
       version: a1
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list rom
       configuration: driver=nouveau latency=0
       resources: irq:48 memory:d2000000-d2ffffff memory:a0000000-afffffff memory:b0000000-b1ffffff ioport:4000(size=128) memory:b2000000-b207ffff
  *-display
       description: VGA compatible controller
       product: 4th Gen Core Processor Integrated Graphics Controller
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:00:02.0
       version: 06
       width: 64 bits
       clock: 33MHz
       capabilities: msi pm vga_controller bus_master cap_list rom
       configuration: driver=i915 latency=0
       resources: irq:47 memory:d3000000-d33fffff memory:c0000000-cfffffff ioport:5000(size=64)
[1]+  Done                    lspci | grep --color=auto VGA
ubuntu@ubuntu:~$ 

```

About mesa-utils, am I supposed to install that on ubuntu 14.04 or elementary? 
Because I tried in ubuntu 14.04 and It didnt find the package.

---

### Post by Stinger on 2014-03-23
Ok, I think we nailed your problem.
It's due to the older kernel, x-server on elementary and your new hybridgraphics,  you should be able to solve it though using the LTS enablement stack
Here is a good howto [HybridGraphics on Ubuntu 12.04]("https://wiki.ubuntu.com/X/Config/HybridGraphics#A12.04.3") ( elementary Luna ). It suggests the stack from raring but I would use the stack from saucy or trusty to get the newest stack for your hardware ;)

Ps.
Just run 'glxinfo | grep render' from cli and it will suggest the package automatically ( haven't tried it on trusty yet )

---

### Post by Stinger on 2014-03-23
Ok, you can't get the lts-trusty stack yet.
Here is howto do it with the lts-saucy stack:

12.04.3

    NVIDIA systems:
[LIST]
[*]        Install the lts-saucy stack ("linux-generic-lts-saucy" and "xserver-xorg-lts-saucy")
[*]
[*]        Make sure that no other NVIDIA driver is installed including bumblebee (keep the nvidia-common package).
[*]        sudo apt-get purge bumblebee-nvidia
[*]
[*]        Install nvidia-319 (or nvidia-319-updates) and nvidia-prime.
[*]        Reboot the system (restarting X won't be enough).
[/LIST]

Hope it works, unfortunately I can't try it myself :)

---

### Post by brent_berghmans2 on 2014-03-23
I did everything you told me to and my elementary OS finally works! 

I can't thank you enough! :D

Also my wifi works, I haven't found any bugs yet because of the new kernel ;)

---

### Post by Stinger on 2014-03-24
You are very welcome, keeps my brain active ;)
It would seem that users with hybrid graphics could benefit from the LTS Enablement stack, in fact it's a must have because elementary Luna ( Precise ) is based on older kernel and x-server.

The [wiki page about HybridGraphics]("https://wiki.ubuntu.com/X/Config/HybridGraphics") is a good howto but needs to be updated to at least saucy. When it comes to laptops and hybrid graphics, the kernel and x-server can't get new enough :) 

You can mark the thread as solved now ( quickly, before a moderator comes and hit you with a stick :biggrin: )

---

### Post by brent_berghmans2 on 2014-03-24
Yep hybrid graphics (or just newer hardware in fact) can cause a lot of problems it seems :p
And luckely I didn't have too much problems with grub because of my dual boot :p
And ok I will I don't wanto to get hit by a stick :( 

Thanks again :D

---

### Post by Stinger on 2014-03-24
In fact the Mods and Admins are quite helpful and understanding, believe me, I know it from experience ;)

---

### Post by antons-u on 2015-01-15
Hi, do you happen to have a solution for intel integrated graphics card as well ?
First of all I get a text version of the options to install, or try without installing. While on my PC which has an AMD graphics card and cpu, I get a graphical option menu.
When I select "Try without installing" The elementary logo shows up, but after that it goes to the Shell.
The error it keeps giving is:
hda_intel: azx_get_response timeout, switching to single_cmd mode: last cmd=0x000f0001

GNU/Linux 3.2.0-51-generic

How do I solve this? I would really like to try Elementary OS

---

