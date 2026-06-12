---
title: "Minecraft plays horribly"
date: 2012-02-20
forum: Gaming &amp; Leisure
---

### Post by TeddyBaschy on 2012-02-20
Alright guys, I just got a new PC and I installed Ubuntu 10. 04, because I won't have enough money for Windows 7 for a little while.

Now the problem is, Minecraft only seems to get about 10-20 FPS on the lowest settings. Now, I know this isn't a problem with my new computers hardware, so I thought I would ask you fine gentlemen.

I had open jdk installed, but that gave me poor performance, so I tried Sun Java and still get pretty bad framerates.

Now, I'm totally new to Ubuntu, and I'm not sure what's wrong. I'm sorry if I haven't given all of the proper info, just let me know what else you need to know.

Thank you in advance.

---

### Post by a2j on 2012-02-20
> **TeddyBaschy said:**
> I know this isn't a problem with my new computers hardware

how do you know this? what is your hardware? I have seen almost new dell laptop, its not slow, but can't play minecraft because of GPU.

---

### Post by regor210 on 2012-02-20
Could you run Minecraft in terminal and post the output?

Howto
If your using the newest Ubuntu 11.10 Oneiric Ocelot just click on the Ubuntu icon on the upper left side of your desk top and type term in the search window to bring up your terminal options. Any of them should work fine.

Ubuntu 10.04
Applications > Accessories > Terminal 

After you have a terminal open just cut and past or type in the line you would like to run minus the $ 

# regular MC
$ cd ~/Downloads/ &&  java -jar minecraft.jar

# ALLOC's 
$ cd ~/.minecraft/ && java -jar minecraft.jar

----------------------------------
Beyond an error there is 
OptiFine C Light for Minecraft 1.1

[http://www.minecraftforum.net/topic/249637-11-optifine-hd-d2-fps-boost-hd-textures-aa-af/](http://www.minecraftforum.net/topic/249637-11-optifine-hd-d2-fps-boost-hd-textures-aa-af/)

I like to use magic launcher to load mods

[http://www.minecraftforum.net/topic/939149-launcher-magic-launcher-096-mods-options-news/](http://www.minecraftforum.net/topic/939149-launcher-magic-launcher-096-mods-options-news/)

$ cd ~/Downloads/ && java -jar MagicLauncher_0.9.6.jar

---

### Post by TeddyBaschy on 2012-02-20
This is what it says, I'm not sure how much of it is relevant


27 achievements
174 recipes

OptiFine_1.1_HD_A
Mon Feb 20 13:53:08 MST 2012
OS: Linux (i386) version 2.6.32-38-generic
Java: 1.6.0_26, Sun Microsystems Inc.
VM: Java HotSpot(TM) Server VM (mixed mode), Sun Microsystems Inc.
LWJGL: 2.4.2
OpenGL: Software Rasterizer version 2.1 Mesa 7.7.1, Mesa Project
OpenGL Version: 2.1
OpenGL Fancy fog: Not available (GL_NV_fog_distance)
setupTexture: "/title/mojang.png", id: 1
Loading: net.java.games.input.LinuxEnvironmentPlugin
Failed to open device (/dev/input/event7): Failed to open device /dev/input/event7 (13)

Failed to open device (/dev/input/event6): Failed to open device /dev/input/event6 (13)

Failed to open device (/dev/input/event5): Failed to open device /dev/input/event5 (13)

Failed to open device (/dev/input/event4): Failed to open device /dev/input/event4 (13)

Failed to open device (/dev/input/event3): Failed to open device /dev/input/event3 (13)

Failed to open device (/dev/input/event2): Failed to open device /dev/input/event2 (13)

Failed to open device (/dev/input/event1): Failed to open device /dev/input/event1 (13)

Failed to open device (/dev/input/event0): Failed to open device /dev/input/event0 (13)

INSTANCE.absAxesIDs is only 63 long, so 63 not contained
Linux plugin claims to have found 1 controllers

Starting up SoundSystem...
Initializing LWJGL OpenAL
    (The LWJGL binding of OpenAL.  For more information, see [http://www.lwjgl.org](http://www.lwjgl.org))
OpenAL initialized.

setupTexture: "/terrain.png", id: 7
TextureFX registered: bo@a60191, texId: 7, index: 237
TextureFX registered: pd@1d6e3d2, texId: 7, index: 205
TextureFX registered: xs@9daa17, texId: 7, index: 14
setupTexture: "/gui/items.png", id: 8
TextureFX registered: ss@102ae84, texId: 8, index: 54
TextureFX registered: hg@4ce427, texId: 8, index: 70
TextureFX registered: ack@16c2c0, texId: 7, index: 206
TextureFX registered: fv@4bd173, texId: 7, index: 238
TextureFX registered: mn@1a3eab6, texId: 7, index: 31
TextureFX registered: mn@867fad, texId: 7, index: 47
setupTexture: "/title/bg/panorama0.png", id: 10
setupTexture: "/title/bg/panorama1.png", id: 11
setupTexture: "/title/bg/panorama2.png", id: 12
setupTexture: "/title/bg/panorama3.png", id: 13
setupTexture: "/title/bg/panorama4.png", id: 14
setupTexture: "/title/bg/panorama5.png", id: 15
setupTexture: "/title/mclogo.png", id: 16
setupTexture: "/gui/gui.png", id: 17
setupTexture: "/gui/particles.png", id: 18
TextureFX removed: bo@a60191, texId: 7, index: 237
TextureFX registered: TextureHDLavaFX@ea3cdf, texId: 7, index: 237
TextureFX removed: pd@1d6e3d2, texId: 7, index: 205
TextureFX registered: TextureHDWaterFX@428527, texId: 7, index: 205
TextureFX removed: xs@9daa17, texId: 7, index: 14
TextureFX registered: TextureHDPortalFX@944dbd, texId: 7, index: 14
TextureFX removed: ack@16c2c0, texId: 7, index: 206
TextureFX registered: TextureHDWaterFlowFX@7bd46a, texId: 7, index: 206
TextureFX removed: fv@4bd173, texId: 7, index: 238
TextureFX registered: TextureHDLavaFlowFX@1b6a053, texId: 7, index: 238
TextureFX removed: mn@1a3eab6, texId: 7, index: 31
TextureFX registered: TextureHDFlamesFX@d7c6bf, texId: 7, index: 31
TextureFX removed: mn@867fad, texId: 7, index: 47
TextureFX registered: TextureHDFlamesFX@392814, texId: 7, index: 47
TextureFX removed: ss@102ae84, texId: 8, index: 54
TextureFX registered: TextureHDCompassFX@1fb2ef9, texId: 8, index: 54
TextureFX removed: hg@4ce427, texId: 8, index: 70
TextureFX registered: TextureHDWatchFX@1635484, texId: 8, index: 70
Loading custom colors: /misc/grasscolor.png
Loading custom colors: /misc/foliagecolor.png
setupTexture: "/gui/background.png", id: 19
Class not present: LightCache
Class not present: forge.ForgeHooksClient
Class not present: ModLoader
setupTexture: "/mob/char.png", id: 21
setupTexture: "/gui/icons.png", id: 22
setupTexture: "/item/largechest.png", id: 23
setupTexture: "/art/kz.png", id: 24
setupTexture: "/particles.png", id: 25
setupTexture: "/mob/sheep.png", id: 26
setupTexture: "/mob/sheep_fur.png", id: 27
Stopping!

SoundSystem shutting down...
    Author: Paul Lamb, [www.paulscode.com]("http://www.paulscode.com")


Also I'm using an i5 2500k, 560 ti, and 8 gigs of ram

I am using the minecraft installer that I found on these forums, if it's relevant.

---

### Post by regor210 on 2012-02-20
These input errors can cause lag. 

“Failed to open device (/dev/input/event7): Failed to open device /dev/input/event7 (13).....”

Run this then Minecraft

$ sudo chmod go=u /dev/input/event*

let me know how it go's.

---

### Post by pbrane on 2012-02-20
Those device opening errors are normal for the LWJGL to issue. It's looking for input devices to control the game. Also you should be using a command line like this to run minecraft:
```

java -Xms1G -Xmx1G -cp minecraft.jar net.minecraft.LauncherFrame

```
You probably need more VM memory to run minecraft than the default.
More than likely your GPU is the problem. 

You can download the minecraft launcher for free from minecraft.net. You'll have to buy the game to play it legally though.

---

### Post by TeddyBaschy on 2012-02-20
Okay, so I ran sudo chmod go=u /dev/input/event*

Now it just crashes and says this

OptiFine_1.1_HD_A
Mon Feb 20 18:38:30 MST 2012
OS: Linux (i386) version 2.6.32-38-generic
Java: 1.6.0_26, Sun Microsystems Inc.
VM: Java HotSpot(TM) Server VM (mixed mode), Sun Microsystems Inc.
LWJGL: 2.4.2
OpenGL: Software Rasterizer version 2.1 Mesa 7.7.1, Mesa Project
OpenGL Version: 2.1
OpenGL Fancy fog: Not available (GL_NV_fog_distance)
setupTexture: "/title/mojang.png", id: 1
Loading: net.java.games.input.LinuxEnvironmentPlugin
INSTANCE.absAxesIDs is only 63 long, so 63 not contained
INSTANCE.absAxesIDs is only 63 long, so 63 not contained
Linux plugin claims to have found 8 controllers

Starting up SoundSystem...
Initializing LWJGL OpenAL
    (The LWJGL binding of OpenAL.  For more information, see [http://www.lwjgl.org](http://www.lwjgl.org))
OpenAL initialized.

setupTexture: "/terrain.png", id: 7
TextureFX registered: bo@9f2588, texId: 7, index: 237
TextureFX registered: pd@41c977, texId: 7, index: 205
TextureFX registered: xs@aa17c3, texId: 7, index: 14
setupTexture: "/gui/items.png", id: 8
TextureFX registered: ss@188f506, texId: 8, index: 54
TextureFX registered: hg@53f0a8, texId: 8, index: 70
TextureFX registered: ack@dca7d0, texId: 7, index: 206
TextureFX registered: fv@8d5a91, texId: 7, index: 238
TextureFX registered: mn@3508c0, texId: 7, index: 31
TextureFX registered: mn@1d183b7, texId: 7, index: 47
setupTexture: "/title/bg/panorama0.png", id: 10
setupTexture: "/title/bg/panorama1.png", id: 11
setupTexture: "/title/bg/panorama2.png", id: 12
setupTexture: "/title/bg/panorama3.png", id: 13
setupTexture: "/title/bg/panorama4.png", id: 14
setupTexture: "/title/bg/panorama5.png", id: 15
setupTexture: "/title/mclogo.png", id: 16
setupTexture: "/gui/gui.png", id: 17
setupTexture: "/gui/particles.png", id: 18
TextureFX removed: bo@9f2588, texId: 7, index: 237
TextureFX registered: TextureHDLavaFX@c707c1, texId: 7, index: 237
TextureFX removed: pd@41c977, texId: 7, index: 205
TextureFX registered: TextureHDWaterFX@ce3b62, texId: 7, index: 205
TextureFX removed: xs@aa17c3, texId: 7, index: 14
TextureFX registered: TextureHDPortalFX@19ccb73, texId: 7, index: 14
TextureFX removed: ack@dca7d0, texId: 7, index: 206
TextureFX registered: TextureHDWaterFlowFX@15b6aad, texId: 7, index: 206
TextureFX removed: fv@8d5a91, texId: 7, index: 238
TextureFX registered: TextureHDLavaFlowFX@b890dc, texId: 7, index: 238
TextureFX removed: mn@3508c0, texId: 7, index: 31
TextureFX registered: TextureHDFlamesFX@12e7cb6, texId: 7, index: 31
TextureFX removed: mn@1d183b7, texId: 7, index: 47
TextureFX registered: TextureHDFlamesFX@fd9b97, texId: 7, index: 47
TextureFX removed: ss@188f506, texId: 8, index: 54
TextureFX registered: TextureHDCompassFX@1de041e, texId: 8, index: 54
TextureFX removed: hg@53f0a8, texId: 8, index: 70
TextureFX registered: TextureHDWatchFX@1e8e5a7, texId: 8, index: 70
Loading custom colors: /misc/grasscolor.png
Loading custom colors: /misc/foliagecolor.png
setupTexture: "/gui/background.png", id: 19
Class not present: LightCache
Class not present: forge.ForgeHooksClient
setupTexture: "/mob/char.png", id: 21
setupTexture: "/gui/icons.png", id: 22
Class not present: ModLoader
#
# A fatal error has been detected by the Java Runtime Environment:
#
#  SIGSEGV (0xb) at pc=0xb6d21971, pid=1760, tid=2008882032
#
# JRE version: 6.0_26-b03
# Java VM: Java HotSpot(TM) Server VM (20.1-b02 mixed mode linux-x86 )
# Problematic frame:
# V  [libjvm.so+0x3b1971]
[error occurred during error reporting (printing problematic frame), id 0xb]

# An error report file with more information is saved as:
# /home/andrew/Downloads/hs_err_pid1760.log
#
# If you would like to submit a bug report, please visit:
#   [http://java.sun.com/webapps/bugreport/crash.jsp](http://java.sun.com/webapps/bugreport/crash.jsp)
#
Aborted

---

### Post by kaldor on 2012-02-20
What graphics card do you have? This matters a lot.

If you use Intel, you might be out of luck. Upgrading to Ubuntu 11.10 through a fresh install *might* help, but no guarantees.

If you use AMD or NVIDIA graphics, then install the proprietary drivers in Jockey.

Edit: just saw you mentioned the 560ti; that's a good card and should really work well. You're sure you've got the drivers installed?

---

### Post by regor210 on 2012-02-20
Ok, restarting will undo
$ sudo chmod go=u /dev/input/event*

Restart and run
# update
$ sudo apt-get update
$ sudo apt-get upgrade

$ sudo apt-get install mesa-utils

# video driver 3D test FPS
$ glxgears

#video card and driver information   
$ lspci -vmk | grep -A 8 -B 2 VGA

And post what you get.


Note.With the magic launcher you need to place the ModLoader 1st in the upper window.
  ModLoader.zip
So it gets loaded, 1st so it can work.

---

### Post by TeddyBaschy on 2012-02-20
Okay, this is gonna sound stupid, keep in mind that I'm very new to Ubuntu, how do I use/find this Jockey to install my drivers.

I feel like a dope.

---

### Post by TeddyBaschy on 2012-02-20
> **regor210 said:**
> Ok, restarting will undo
$ sudo chmod go=u /dev/input/event*

Restart and run
# update
$ sudo apt-get update
$ sudo apt-get upgrade

$ sudo apt-get install mesa-utils

# video driver 3D test FPS
$ glxgears

#video card and driver information   
$ lspci -vmk | grep -A 8 -B 2 VGA

And post what you get.


Okay so I did all that, and with the gears I got
gears
3491 frames in 5.0 seconds
4005 frames in 5.0 seconds
3800 frames in 5.0 seconds
3904 frames in 5.0 seconds
4019 frames in 5.0 seconds
4171 frames in 5.0 seconds
4094 frames in 5.0 seconds
3991 frames in 5.0 seconds
4035 frames in 5.0 seconds
3523 frames in 5.0 seconds
3527 frames in 5.0 seconds
3495 frames in 5.0 seconds
3466 frames in 5.0 seconds

video card and driver info

Device:    01:00.0
Class:    VGA compatible controller
Vendor:    nVidia Corporation
Device:    Device 1200
SVendor:    eVga.com. Corp.
SDevice:    Device 1568
Rev:    a1
Module:    nvidiafb
Module:    nouveau

---

### Post by kaldor on 2012-02-20
> **TeddyBaschy said:**
> Okay, this is gonna sound stupid, keep in mind that I'm very new to Ubuntu, how do I use/find this Jockey to install my drivers.

I feel like a dope.

We all start somewhere :)

System menu > Administration > Additional drivers.

Edit: yep, you're running Nouveau. It's the default open source driver, but lacks in 3d performance and power management. That would explain everything.

---

### Post by TeddyBaschy on 2012-02-20
> **kaldor said:**
> We all start somewhere :)

System menu > Administration > Additional drivers.

Edit: yep, you're running Nouveau. It's the default open source driver, but lacks in 3d performance and power management. That would explain everything.


I went to system>administration> but there was no "additional drivers" area

There was a "hardware drivers" but when I ran it, it says "no proprietary drivers are in use on this system"

I don't know if I mentioned it, but I'm on 10.04.

---

### Post by kaldor on 2012-02-20
> **TeddyBaschy said:**
> I went to system>administration> but there was no "additional drivers" area

There was a "hardware drivers" but when I ran it, it says "no proprietary drivers are in use on this system"

I don't know if I mentioned it, but I'm on 10.04.

Yeah, that's a bit odd. I guess you could try installing the drivers manually. Grab them from the NVIDIA website and see what you can do.

In a worst-case scenario, you could install Ubuntu 11.10 fresh- it might have better support for newer hardware.

---

### Post by regor210 on 2012-02-20
When you open Hardware Drivers you should see 3 circles with a NVIDIA driver next to each of them.
Click on the one that says [Recommended] at the end and install it.

or is there noting in the Window?

---

### Post by TeddyBaschy on 2012-02-20
> **regor210 said:**
> When you open Hardware Drivers you should see 3 circles with a NVIDIA driver next to each of them.
Click on the one that says [Recommended] at the end and install it.

or is there noting in the Window?

Everything is completely blank. Nothing anywhere in the boxes.

---

### Post by regor210 on 2012-02-20
If I were a betting man I would bet that your Nvidia video card is so new that its not supported by the kernel used in Ubuntu 10.04. Do you have any idea what card you have? 

Installing Nvidia drivers by hand is a bit tricky and has to be reinstalled with every kernel update or your likely to get dumped into a command line system $.

If you like I will tell you how I do it, but if it were me I would use 11.04 for Gnome 2 or 11.10 Unity.

---

### Post by TeddyBaschy on 2012-02-21
Okay, so I installed 11.04 and I've got a new problem.

The image on my monitor is too large, and going into system settings> display doesn't fix it either.

I've installed the version current and recommended drivers for my 560 ti also. Any help?

Also, to be more specific about the problem, I can just barely see the edges of my panels, but most of them have vanished off the edge of my screen.

PS I'm aware that this is venturing into an off topic area, but I need to fix this before I can get MC working.

---

### Post by regor210 on 2012-02-21
Can you get into System > Adninistration > Nvidia X Server Settings

> X Server Display Configuration 

Resolution > Then move the slider to your monitors settings?

---

### Post by TeddyBaschy on 2012-02-22
Got it working, thanks to everyone who helped!

---

