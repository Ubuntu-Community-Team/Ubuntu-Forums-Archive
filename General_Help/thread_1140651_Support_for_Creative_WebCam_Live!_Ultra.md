---
title: "Support for Creative WebCam Live! Ultra"
date: 2009-04-27
forum: General Help
---

### Post by maheshasolkar on 2009-04-27
I have a Creative WebCam Live! Ultra USB camera connected to my desktop. It has always been, since I use it when I boot XP on the computer. It has always been unsupported on Linux, at least based on the following:

  [http://opensource.creative.com/webcam.html](http://opensource.creative.com/webcam.html)

After installing Jaunty in the last couple of days, I see the green LED on the camera glow! I had never seen that before in Ubuntu (Intrepid). I tried to use cheese, but it does not detect the camera.

Has something changed in Jaunty, regarding Creative web cam support? Is it just a green light or a glimmer of home for this web cam in question?

---

### Post by spiderbatdad on 2009-04-27
seems like a glimmer of hope. could you post the output of lsusb, so we can see the device id?

---

### Post by maheshasolkar on 2009-04-28
Back to the computer... here's the output of lsusb:

```
**Bus 002 Device 002: ID 041e:403c Creative Technology, Ltd WebCam Live! Ultra**
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 008 Device 003: ID 045e:00db Microsoft Corp. Natural Ergonomic Keyboard 4000 V1.0
Bus 008 Device 002: ID 046d:c00e Logitech, Inc. M-BJ58/M-BJ69 Optical Wheel Mouse
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 002: ID 056a:0042 Wacom Co., Ltd Intuos 2 6x8
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

```

---

### Post by ndefontenay on 2009-04-28
I think I got the same. Worked out of the box with cheese.

My problem is with skype where I will see just a green noise when I test it.

I think it's skype related since they didn't release a Jaunty version yet. I'm waiting patiently for now. Quite problematic though because Skype is the only reason why I would use a webcam.

---

### Post by maheshasolkar on 2009-04-28
> **ndefontenay said:**
> I think I got the same. Worked out of the box with cheese.

My problem is with skype where I will see just a green noise when I test it.

I think it's skype related since they didn't release a Jaunty version yet. I'm waiting patiently for now. Quite problematic though because Skype is the only reason why I would use a webcam.

Can you share the output of your 'lsusb'?

---

