---
title: "Enabling Beryl on Dell Vostro 1510"
date: 2009-04-21
forum: General Help
---

### Post by Guillaumeb on 2009-04-21
I have 9.04 on a Dell Vostro 1510
It has the GM965/GL960 Integrated graphic controller

This is a pretty fresh install so I dunno if the needed drivers are installed

Do you know where I should be starting ?

Thanks

---

### Post by codeseer on 2009-04-21
Beryl is now Compiz-Fusion.

You'll want to open Synaptic and make sure all of the updates are applied.

To check the drivers go to System->Administration->Hardware Drivers.

Edit:

To get Compiz-Fusion, you'll want to fire up Synaptic and search for 'compiz'. You'll want to get both the 'compiz' and the 'compizconfig-settings-manager' packages.

This contains the long version of what I just told you: [https://help.ubuntu.com/community/CompositeManager/CompizFusion]("https://help.ubuntu.com/community/CompositeManager/CompizFusion")

---

### Post by Guillaumeb on 2009-04-21
Thanks for your quick reply, I appreciate.

I did what you said and checked the terminal installation tutorial

I'm still  getting the error: "graphics could not be enabled"

Searching this forum I realize there used to  be a problem with my graphic card. Wondering if it has been fixed or not. Those threads are like two years old.

---

### Post by codeseer on 2009-04-21
If you changed the drive in the 'Hardware Drivers' window, you'll probably need to restart for that to take effect. It's my understanding that the Intel based video is handled by Ubuntu and you don't need to go out and find a specific driver for them.

---

### Post by northern lights on 2009-04-21
Can you please post the output of```
sudo lshw -C display
```Thank you.

---

### Post by Guillaumeb on 2009-04-21
Thanks for coming back to me. I did restart and got the same error message. Running the command line returns

 *-display:0 UNCLAIMED   
       description: VGA compatible controller
       product: Mobile GM965/GL960 Integrated Graphics Controller
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:00:02.0
       version: 0c
       width: 64 bits
       clock: 33MHz
       capabilities: msi pm bus_master cap_list
       configuration: latency=0
  *-display:1 UNCLAIMED
       description: Display controller
       product: Mobile GM965/GL960 Integrated Graphics Controller
       vendor: Intel Corporation
       physical id: 2.1
       bus info: pci@0000:00:02.1
       version: 0c
       width: 64 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list
       configuration: latency=0

---

### Post by northern lights on 2009-04-21
mkey.

Currently, the device has not been assigned a driver at all.

Please run ```
sudo apt-get update && sudo apt-get install xserver-xorg-video-intel
```

What release are you on?

---

### Post by Guillaumeb on 2009-04-21
alright now it says 

xserver-xorg-video-intel is already the newest version.
The following packages were automatically installed and are no longer required:
  libaudio2
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

I am on 9.04 RC downloaded yesterday

---

### Post by northern lights on 2009-04-21
Fair enough - the driver is installed, just not assigned.

As codeseer had suggested, you checked the *Hardware Drivers* menu entry. What exactly did you see / select?

---

### Post by cariboo on 2009-04-21
I have Intrepid installed on a system with the same chipset, I get the unclaimed message when running,

```
lshw -C Display
```

The driver for the graphics adapter is built in to the kernel so it looks like a driver isn't loaded. I have compiz enabled and get all the effects.

I think the OP's problem is related to Jaunty intel graphics drivers, have a look [here]("http://www.ubuntu.com/getubuntu/releasenotes/904") under Other Know Issues.

Jim

---

### Post by Guillaumeb on 2009-04-21
Ok i had to go out for an hour tdentidt!) Will definitely check that when back home and report to you after. Thanks for your help

---

### Post by northern lights on 2009-04-21
> **cariboo907 said:**
> I get the unclaimed message when running,

```
lshw -C Display
```

The driver for the graphics adapter is built in to the kernel so it looks like a driver isn't loaded.
Never seen that behaviour, but never had a GM9XX chipset either. Just setup a Dell XPS One with a GMA33/35 - nothing the like happened in either Intrepid or Jaunty.

Anyhow, should that be the case, I can't be of further help - how do you figure what's the issue now?

---

### Post by Guillaumeb on 2009-04-21
Going to the hardware drivers menu this is what I get:

[http://www.singlehostimage.com/showpic-1149/hdw.png](http://www.singlehostimage.com/showpic-1149/hdw.png)

---

### Post by codeseer on 2009-04-21
> **Guillaumeb said:**
> Going to the hardware drivers menu this is what I get:

[http://www.singlehostimage.com/showpic-1149/hdw.png](http://www.singlehostimage.com/showpic-1149/hdw.png)

Yeah, normally you would have a video driver listed under that; but as Cariboo said, it's evidently built into the kernel.

---

### Post by Guillaumeb on 2009-04-21
OK, so the graphic drivers are built within the system but not assigned to my hardware. So do you think it is possible to install another driver or to assign it ?

Should I proceed to the steps mentioned on [this page]("https://wiki.ubuntu.com/JauntyJackalope/ReleaseNotes#Other%20known%20issues") in the section titled "Performance regressions on Intel graphics cards"

---

### Post by Sinner on 2009-05-01
If you still in trouble with that try this:
(its worked for me on dell vostro 1510 with ubuntu 9.04)

On vostro the chipset for graphic is an intel 965, which is blacklisted:
[http://wiki.compiz-fusion.org/Hardware/Blacklist](http://wiki.compiz-fusion.org/Hardware/Blacklist)

to bypass this edit the compiz config file:
sudo gedit /usr/bin/compiz

and comment the line (add a #)
T="$T 8086:2a02 " # Intel GM965

details here :
[http://www.searchmarked.com/ubuntu/how-to-enable-compiz-fusion-on-ubuntu-710-if-your-video-card-is-blacklisted.php](http://www.searchmarked.com/ubuntu/how-to-enable-compiz-fusion-on-ubuntu-710-if-your-video-card-is-blacklisted.php)

---

