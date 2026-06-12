---
title: "Dolphin Shows Black Screen when Emulating Game"
date: 2013-05-23
forum: Emulators
---

### Post by King Dude on 2013-05-23
Version: Dolphin 3.5-1372 x64
Game: Twilight Princess [GC]
Video Card: ATI Radeon HD4350
Operating System: Ubuntu 13.04 x64

When I begin to play the game, it appears to start, but hangs in a black screen at 30-60fps. If I try to exit the program, it will freeze and I need to force quit it. Any ideas or suggestions on what is happening?

---

### Post by Lightning Dragon on 2013-05-23
Hi,

CPU? And how are your settings? Try switching the back-end graphics to DX9, adjust the internal res (I cannot tell you which because it will depend on your computer, so just try 2x or 3x) and disable AA as well as try to disable external frame buffer. Reset, turn off and then try to open the game again.

And I'm assuming you are using the Linux port? Which version?

---

### Post by King Dude on 2013-05-23
It does not support DirectX backends because I'm running it on Linux, just OpenGL. My processor is a Core 2 Quad 2.33Ghz and the emulator version is Dolphin 3.5 build 1372 for Ubuntu.

As for settings, I'll post them once I fire up my machine in a little bit (I'm on my laptop).

---

### Post by King Dude on 2013-05-24
All of this is checked in my settings:

-Enable dual core
-Enable Idle Skipping
-JIT  recompiler
-DSP HLE Emulation
-Audio Backend: ALSA
-Graphics Backend: OpenGL
-Scaled EFB Copy
-EFB Copies: Texture
-Cache Display List
-OpenMP Texture Decoder

---

### Post by Lightning Dragon on 2013-05-24
Hi,

Have you installed drivers for your graphics card? And are you attempting to run the Wii version or the Gamecube version? A lot of people have problems with the Wii version and have found the Gamecube version to work. When I get to my Linux computer I will check out further solutions for you.

---

### Post by King Dude on 2013-05-24
I have the gamecube version, the only version worth playing :P. And I am running generic drivers for my ATI Radeon HD4350, not AMD's propriety drivers.

---

### Post by Lightning Dragon on 2013-05-24
Hi,

Alright, that's the version I'm running right now as well. Though I installed Nvidia's *official* drivers with an AMD Athlon II X2 CPU and GeForce 8600GT and can get into the game with a near constant 30 FPS on one computer, and also got the same FPS on a install of Ubuntu that has Ubuntu drivers. So let us see if these settings help you emulate something similar or help. Keep in mind some of the things will be different for you like resolution;

Advanced:
[http://s17.postimg.org/khi92ye33/advanced.png](http://s17.postimg.org/khi92ye33/advanced.png)

Audio:
[http://s17.postimg.org/wfjtguhu7/audio.png](http://s17.postimg.org/wfjtguhu7/audio.png)

Enhancements:
[http://s17.postimg.org/dpru03p3j/enhancements.png](http://s17.postimg.org/dpru03p3j/enhancements.png)

General:
[http://s17.postimg.org/m6rcb0tsf/general.png](http://s17.postimg.org/m6rcb0tsf/general.png)

Hacks:
[http://s17.postimg.org/6p3u7bnbj/Hacks.png](http://s17.postimg.org/6p3u7bnbj/Hacks.png)

(Options) General:
[URL="http://s17.postimg.org/mbv3kp13j/Options_general.png"]http://s17.postimg.org/mbv3kp13j/Options_general.png

[/URL]
I used Dolphin 3.0-776 and your version, by the way.

There are problems with the game that cannot be fixed like the map issue and the terrible FPS in Hyrule field, and the sunrays. Some of these things might be worse for you, though.

---

### Post by King Dude on 2013-05-25
My problem is that the game does not even show anything- just a black screen.

---

### Post by Lightning Dragon on 2013-05-25
Hi,

I know. I was hoping changing your settings would let you get passed that problem. So may I assume it didn't work? 

[SIZE=1]Oh, and the last bit was just so if you encounter those errors you would know solutions/or that they are universal problems.[/SIZE]

---

### Post by King Dude on 2013-05-25
Yeah I checked, my settings are just like those above and it still does not work. I'm thinking it's a problem with my video card.

---

### Post by Lightning Dragon on 2013-05-26
Hi,

I just looked into your card. I found many reviewers and comments saying it isn't meant for gaming other than real light stuff, so I'm guessing it is your GPU as well. Though I am no expert on the matter, it does seem like the cause of your problems.

---

### Post by King Dude on 2013-05-26
It should still work though. It's performance may be crappy at best, but it should work regardless.

---

### Post by Lightning Dragon on 2013-05-26
Hi,

Have you considered it might be your ISO? You might have improperly ripped it. Other than that, would you be willing to try the Windows version of Dolphin via Wine? Latest build with settings listed below?

_(Options Config)_
**General:**
JIT recompiler (recommended)
Enable Idle Skipping
[U]
(Graphics config)[/U]
**General:**
Uncheck V-Sync (*Also do this for your graphics card if possible*)

**Enhancements:**
Anti-Aliasing > none
Anisotropic > 1X
And make sure nothing is checked below those options

**Hacks:**
Check the following; Ignore Format Changes, Disable (under EFB Copies), Disable (under External Frame Buffer), Cache Display Lists.
Also turn Texture Cache to FAST

_(DSP config)_
**Audio:**
DSP HLE Emulation (fast) < this is because you have to compile the other LLE sound by yourself
Audio Backend > XAudio2

Now right-click the Twilight Princess ISO while in Dolphin and then go into properties and make sure _only_ *ZTP Hack* is checked and *Speed Up Disc transfer*.

---

### Post by King Dude on 2013-05-26
I suppose it could be the ISO. Unfortunately I got the ISO from my best friend who is in possession of our Gamecube and Twilight Princess, and when he sent it to me he split it into multiple Rar files. I think when I tried putting them back together Ubuntu's default unpacker screwed up somehow.

Sigh. If my damn flashdrive could connect to my Linux machine, I would unpack them in Windows and then carry it over.

By the way, why doesn't my my Fat32 flashdrive not want to connect? Is Windows screwing with me by making it Windows-only compatible when it formatted it?

---

### Post by Lightning Dragon on 2013-05-26
Hi,

Whenever you can reattempt your burn and come back to the issue, please update us on your problems/solution. Though if it still persists even after our tinkering, would you consider consulting the Dolphin forum or an emulator forum about the issue?

As for your flash drive, it shouldn't be. I have never heard of a flash drive being turned into Windows only by Windows. Have you tried another USB port? Or maybe navigating your media folder for the USB stick?

---

### Post by King Dude on 2013-05-26
I've tried multiple ports for my flashdrive, but to no avail.

---

### Post by Lightning Dragon on 2013-05-26
Hi, 

This is quite strange. What kind of flash drive is it? And did you try to navigate to the media folder to see if it is there? It should automatically mount, but it might be turned off for you. Please view this link;

[https://help.ubuntu.com/community/Mount/USB](https://help.ubuntu.com/community/Mount/USB)

You can also try mounting via the terminal;

[http://askubuntu.com/questions/37767/how-to-access-a-usb-flash-drive-from-the-terminal](http://askubuntu.com/questions/37767/how-to-access-a-usb-flash-drive-from-the-terminal)
[http://askubuntu.com/questions/90976/usb-drive-not-mounting](http://askubuntu.com/questions/90976/usb-drive-not-mounting)

---

### Post by King Dude on 2013-05-26
I tried lsusb, it did not work. It's a standard encrypted flash drive formatted with FAT32.

---

### Post by Lightning Dragon on 2013-05-27
Hi,

Brand name of the USB, or is it a generic cheap brand? That could very well be the issue. Also, did you try going into your media folder? In the first link, don't follow the steps under "Other Useful Commands" yet. Your system isn't detecting your USB/mount so I doubt that will return anything for you. If you know the name of the device, you can try to manually mount the USB drive. Let us see if automatic mounting is enabled first. Open up your terminal and write/paste the following commands;

```
dconf-editor
```

This should bring up what you need to edit. If you are given errors, please share them. If you aren't given errors, continue. Next browse for "org.gnome.desktop.media-handling" and see if "automount" is set to _**true**_. If it isn't, set it to true. Reboot your computer and plug your USB into a port and see if anything pops up. If nothing does, continue with the following steps to _manually_ mount. Run this command while the USB is plugged in;

```
sudo fdisk -l
```

This should list your device name(s) which should resemble something like "/dev/sdb1" etc etc remember the name _exactly_ and write it down if you need to. Next we need to create a folder for the mounting, so put this into the terminal next;

```
sudo mkdir /media/usb
```

Now this is where the name of the device comes in. Once you have the device name, do this command, switching out "/dev/sdb1" with the name of the device you got via "sudo fdisk -l";

```
sudo mount /dev/sdb1 /media/usb
```

If that goes well, then use this command to mount the USB;

```
sudo umount /media/usb
```

[SIZE=1]*When you do the sudo command to list devices, please make sure you have any other USB drives, external books or the like disconnected so you will know which it is you are looking for.*[/SIZE]

If none of that works, you can try [Disk Utility]("https://apps.ubuntu.com/cat/applications/natty/gnome-disk-utility/") to see if the USB is mounted and working. If none of that works, then I think it might be your brand or a faulty USB stick.

---

### Post by King Dude on 2013-05-27
The brand is "Memory Master." It's a cheap flash drive that I bought at Fry's Electronics one day, but it's never been giving me problems before.

---

### Post by Lightning Dragon on 2013-05-27
Hi,

I have never heard of it. It might be the issue, even if it works in Windows. Have you tried the above? If so, what were the results? Any errors?

---

### Post by King Dude on 2013-05-27
I'll try it once I'm on my Ubuntu machine.

---

### Post by Linuxgamer94 on 2013-07-31
Hello freind, I think I know the problum, but you willn't like it. I had the exact issue happen nomatter what version, Wine/linux ports of Dolphin. Most of the times it is the ISO. It was probaly corupted to begin with. I have had this issue happen over and over again and most of the times it was the ISO's.

---

