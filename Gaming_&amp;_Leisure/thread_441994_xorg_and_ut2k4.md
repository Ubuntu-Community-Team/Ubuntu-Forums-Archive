---
title: "xorg and ut2k4"
date: 2007-05-13
forum: Gaming &amp; Leisure
---

### Post by MikeReiner on 2007-05-13
I have a strange issue.

UT2004, for some reason, when running as a client (not hosting a server) will cap it's frame rate at whatever the refresh rate is. Now thats fine and dandy... except for me it caps it at 50.. yet my refresh rate is 85. Now before any of you start telling me to quit whining and that 50 is a perfectly playable frame rate (and it is), but playing like this gives me a head ache. The monitor is displaying the same frame in my eyes multiple times before it advances to the next one, and it really hurts after about 10 minutes.

I find that in the screen resolution preferences, it says iI'm using 1280x1024 @ 50hz.. but the monitor is actually running at 85Hz. 

I don't understand why it would do this, and I've been trying to follow this guide [http://ubuntuforums.org/showthread.php?t=83973](http://ubuntuforums.org/showthread.php?t=83973)
for about an hour.. and every time I make the supposed modification to the xorg.conf, I end up at a black screen of text... and have to run sudo nano /etc/X11/xorg.conf and remove the lines I added to get x running again..

any thoughts on this one? my current xorg conf is here: [http://paste.ubuntu-nl.org/20616/](http://paste.ubuntu-nl.org/20616/)

for the record, my monitor is a 19" CRT, I typically use:
1024x768 @ 85Hz
1280x1024 @ 85Hz and
1600x1200 @ 75Hz

---

### Post by Enverex on 2007-05-13
It's because of nVidia's TwinView. It's not really running at 50hz but it is probably running at 60 which isn't much better on a CRT.

Change the device section to look like this:

Section "Device"
    Identifier     "nVidia Corporation G70 [GeForce 7600 GT]"
    Driver         "nvidia"
    Option        "TwinView" "0"
EndSection

---

### Post by Cappy on 2007-05-13
The frame rate cap is the (number of incoming packets from the server) x 2. If you're getting 50 FPS then you're getting 25 packets per second. You can't increase this because it is a limitation of the unreal engine. On very large servers sometimes the FPS is equal to the amount of incoming packets, but I've only seen this happen on a 32 player AS server called Omnipotents.

Edit:
I noticed you want to change your refresh rate.
I only know the command for nvidia cards:
```

nvidia-settings

```
ATI has a control panel that probably does the same thing.

---

### Post by MikeReiner on 2007-05-13
> **Cappy said:**
> The frame rate cap is the (number of incoming packets from the server) x 2. If you're getting 50 FPS then you're getting 25 packets per second. You can't increase this because it is a limitation of the unreal engine. On very large servers sometimes the FPS is equal to the amount of incoming packets, but I've only seen this happen on a 32 player AS server called Omnipotents.

Edit:
I noticed you want to change your refresh rate.
I only know the command for nvidia cards:
```

nvidia-settings

```
ATI has a control panel that probably does the same thing.

Well I fixed the refresh rate but no change.

I find this puzzling.. I get 85 fps in windows.. and if the fps is twice the packets.. does that mean I get less packets in linux?

---

### Post by Eazy© on 2007-05-13
Is this on both off-line and on-line? 

I know I had this trouble _only_ on-line when I was using Kubuntu Breezy. Off-line I had correct fps. The way I fixed it was to install the i386 kernel instead of the k7-kernel. Now there are no choices of kernels if I understand it right (I always compile my own kernel now days (i486)), so the possible solution is to compile your own kernel, that's what I did. I could never figure out what the trouble was, nor could anybody else.

---

### Post by MikeReiner on 2007-05-13
Offline works beautiful.. almost always atleast 120 fps.

How would I go about recompiling the kernal to fix this?

---

### Post by Cappy on 2007-05-13
It should be the same as Windows (or at least mine is). It depends on what server you goto because the server's tick rate varies from server to server. The tick rate is usually between 30-40 on most servers (60-80fps).
You can press F6 in-game to see the number of your inbound packets.

I wouldn't think recompiling your kernel would bypass the engine's limitation but anything is possible in the land of linux ^^

---

### Post by Eazy© on 2007-05-13
Its not that easy to compile your own kernel, but I use [this]("http://ubuntuforums.org/showthread.php?t=311158") guide. You probably have to compile more than one time as things might stop working for you, I know it did for me. When you compile, be sure to pick i486-kernel in xconfig and not k7-kernel (if you got an AMD processor) you also have to install nvidia drivers again. I always use the drivers from nvidia.com

I made a [tips/hints for UT2004]("http://ubuntuforums.org/showthread.php?t=374469") where I mention a couple of tips. Most of it (if not all) is not necessary.

---

### Post by Eazy© on 2007-05-13
> **Cappy said:**
> I wouldn't think recompiling your kernel would bypass the engine's limitation but anything is possible in the land of linux ^^
I know its strange, no one could explain it. I tested all kernels available in repository with both graphic drivers from nvidia.com and nvida-glx in repository without making any changes on UT2004. The only once that worked was the i386-kernel from repository and the i486-kernel I compiled myself. I wanted the i486-kernel because I have a AMD dual core CPU.

---

### Post by MikeReiner on 2007-05-13
> **Eazy© said:**
> I know its strange, no one could explain it. I tested all kernels available in repository with both graphic drivers from nvidia.com and nvida-glx in repository without making any changes on UT2004. The only once that worked was the i386-kernel from repository and the i486-kernel I compiled myself. I wanted the i486-kernel because I have a AMD dual core CPU.

It doesn't matter what server I play in, it's ALWAYS 50 fps.. even when I play with my friend hosting. .. same guy.. 85 windows and 50 in linux.

my CPU is an AMD64 4200X2 dual core.

i'll look over those guides, thanks.

---

### Post by Enverex on 2007-05-14
Do you have V-Sync turned on?

---

### Post by Eazy© on 2007-05-14
> **Enverex said:**
> Do you have V-Sync turned on?
If he get 120 fps @ 85hz off-line it means v-sync is turned off.

---

### Post by Enverex on 2007-05-14
> **Eazy© said:**
> If he get 120 fps @ 85hz off-line it means v-sync is turned off.

Ah, didn't notice that. If this is all true that's a bizzare way of running the engine...

---

### Post by Cappy on 2007-06-03
I found this today:
[http://purehighspeed.com/forum/showthread.php?t=55](http://purehighspeed.com/forum/showthread.php?t=55)

It increases the bandwidth to the server which increases the in-game FPS.

---

