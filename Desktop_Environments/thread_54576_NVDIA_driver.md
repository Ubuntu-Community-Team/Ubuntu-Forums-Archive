---
title: "NVDIA driver"
date: 2005-08-05
forum: Desktop Environments
---

### Post by Owdy on 2005-08-05
I installed driver like this: [http://ubuntuguide.org/#installnvidiadriver](http://ubuntuguide.org/#installnvidiadriver)

cat /proc/driver/nvidia/agp/status
Gives me 'Status:          Disabled'. 

Why is that? How do i enable it?

---

### Post by Lord Illidan on 2005-08-05
Try re-starting the x graphical environment, by running in a terminal:

```
sudo /etc/init.d/kdm stop
```

and afterwards

```
sudo /etc/init.d/kdm start
```

And did u run this:

```
sudo nvidia-glx-config enable
```

---

### Post by Owdy on 2005-08-05
okay, now i get

osku@koti:~$ cat /proc/driver/nvidia/agp/status
Status:          Enabled
Driver:          AGPGART
AGP Rate:        4x
Fast Writes:     Disabled
SBA:             Disabled


is that ok?

---

### Post by polo_step on 2005-08-05
[QUOTE=Owdy]
Fast Writes:     Disabled[/QUOTE]
Curiously, I just checked mine and saw "Fast Writes" disabled, too.

What is this setting and what does it mean?  Should it be switched on?

Thanks for any help.
===========================================
anonymous@beatdown:~$ cat /proc/driver/nvidia/agp/status
Status:          Enabled
Driver:          AGPGART
AGP Rate:        8x
Fast Writes:     Disabled
SBA:             Enabled

---

### Post by Lord Illidan on 2005-08-05
Same as mine. Fast  writes are enabled from the BIOS not from Linux, I believe, but I don't think the increase in performance is that noticeable.
Have you tried running glxgears to see if gl performance is satisfactory?

```
glxgears
```

---

### Post by Owdy on 2005-08-05
Fast Write is enabled in BIOS.

---

### Post by polo_step on 2005-08-06
[QUOTE=Lord Illidan]Same as mine. Fast  writes are enabled from the BIOS not from Linux, I believe...[/quote]
Yes, that's right. I remember now.  I don't retain this stuff like I used to.  :-| 

> Have you tried running glxgears to see if gl performance is satisfactory?
Yeah, it's around 1340+/-, which I understand is not bad.

---

### Post by drizek on 2005-08-06
[QUOTE=polo_step]Yes, that's right. I remember now.  I don't retain this stuff like I used to.  :-| 


Yeah, it's around 1340+/-, which I understand is not bad.[/QUOTE]
 what card do you have? i get about 6000 on a 6600gt, so does that seem about right? 

also, fastwrites are bad IIRC. they have a minor speed improvement, but cause crashing and instability(i could be mixing it up with some other thing though).

---

### Post by f1dave on 2005-08-06
drizek: Yes, that's about right.

I average ~6050 for my 6600GT running on an nforce2 mobo with a 2500XP athlon.

---

### Post by polo_step on 2005-08-06
[QUOTE=drizek]what card do you have? i get about 6000 on a 6600gt, so does that seem about right? [/QUOTE]
A BFG GeForce FX5500oc 128.  CPU in this Linux box is an AMD Sempron 2200.

Ha!  I've been doing it wrong (why are you not surprised?).  Here's what's really happening with the test being done offscreen:

anonymous@beatdown:~$ glxgears
5595 frames in 5.0 seconds = 1119.000 FPS
6962 frames in 5.0 seconds = 1392.400 FPS
6967 frames in 5.0 seconds = 1393.400 FPS
[offscreen now...]
20280 frames in 5.0 seconds = 4056.000 FPS
20286 frames in 5.0 seconds = 4057.200 FPS
20280 frames in 5.0 seconds = 4056.000 FPS
20278 frames in 5.0 seconds = 4055.600 FPS
20266 frames in 5.0 seconds = 4053.200 FPS
20275 frames in 5.0 seconds = 4055.000 FPS
20277 frames in 5.0 seconds = 4055.400 FPS

---

