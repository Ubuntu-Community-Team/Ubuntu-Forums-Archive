---
title: "3D cube - Skydome Field Of View broken"
date: 2015-12-28
forum: Desktop Environments
---

### Post by kiklo on 2015-12-28
I couldn't find anyone posting this problem online.

I managed to turn on the 3D cube and everything around it. But the skydome displays broken. I can verbally identify the problem as it's a common thing in gaming and 3D graphics in general.
The camera's field of view value is too low/high (probably zero / 180°). In a decent game engine you change a single value to fix the fov. I know ubuntu isn't a gaming engine, but still isn't there a config file that I could change, or does anyone know how the skydome functions?

I recently upgraded to NVIDIA's 358.16 graphic driver, but I don't know if the skydome worked before, didn't try to enable it with other drivers.

As I said, everything seems to work. You can see in the background it rotates correctly and everything. All except for the field of view.

*Oh yeah, and I already tried resetting the compiz settings, which seemed to help lot of people, but nothing changed.*

[IMG]http://orig15.deviantart.net/aa79/f/2015/362/7/a/fov_by_swift502-d9lstvn.jpg[/IMG]

---

### Post by egeezer on 2015-12-28
If you mean the combined field of view (image of the cube and its skydome in the frame of the monitor), you alter that by setting the zoom value in the Rotate Cube setting.  If you set it >1, the cube will cover a smaller part of the overall FOV.

---

### Post by kiklo on 2015-12-28
The cube is fine. It has correct size and everything.
The background is wrong. The space image in the background should stretch across the whole screen, revealing 30°, 45° or something like that of the skydome. Instead we get to see 180° of it.

---

### Post by egeezer on 2015-12-28
Okay, now I see what you mean.  If you resize/reshape the sky image you're using as the skydome as if it were a regular background image, it will work out fine.  The image you are using seems to have an aspect ratio that won't work.

---

### Post by kiklo on 2015-12-28
Thanks. I tried resizing the image to screen resolution (1366x768), which is 16:9, also setting the image size to powers of two (2048x1024), and even 1:1 (512x512). The problem persists.

Also switched to following drivers:
[I]NVIDIA binary driver 352.63 (proprietary)
[/I]*NVIDIA binary driver 355.11 (open source)*[I]
NVIDIA binary driver 358.16 (open source)
[/I]But it made no difference. So I hope I can exclude graphic driver as the cause...

---

### Post by deadflowr on 2015-12-28
Various aspects of cube die and come back, almost routinely.
Here's one bug on skydome:
[https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/1330080](https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/1330080)

---

### Post by hnoor0033 on 2016-01-27
[COLOR=#000000]Thanks. I tried resizing the image to screen resolution (1366x768), which is 16:9, also setting the image size to powers of two (2048x1024), and even 1:1 (512x512). The problem persists.



____________________
[/COLOR]Play Online solitaire Game visit [solitire](http://www.solitairewithbuddies.com) for more details.

---

