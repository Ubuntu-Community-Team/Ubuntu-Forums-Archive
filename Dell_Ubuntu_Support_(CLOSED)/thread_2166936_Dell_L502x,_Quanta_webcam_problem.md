---
title: "Dell L502x, Quanta webcam problem"
date: 2013-08-11
forum: Dell Ubuntu Support (CLOSED)
---

### Post by thanasvel on 2013-08-11
I have a problem with my webcam from my laptop on ubuntu 12.04
Dell XPS 15 L502x, Webcam : Quanta computers

The problems:
1. Periodically the image freezes in skype call
2. After some time although the webcam start ( light next to lens ) I get only a
    black image. The problem starts with skype and then all other programs have problems
    ( guvcview, cheese ) and have a black image

I have to restart my laptop to windows to get it working, or turn off the laptop for some time. 
This problems never appears when I am using the webcam in windows.
And it more frequent now. No process ([FONT=courier new] lsof /dev/video0 [FONT=arial])[/FONT][/FONT] appears to be using the webcam.

And with guvcview i get: 
[FONT=courier new]Could not grab image (select timeout): Resource temporarily unavailable 
[/FONT]
I even tried reloading the module with no luck:
[FONT=courier new]modprobe -r uvcvideo[/FONT]
[FONT=courier new]modprobe uvcvideo[/FONT]

It might seem a hardware error and not software error, as sometimes by moving my laptop 
screen back and forth it unfreezes the image. But these problems never occur in windows.

Any ideas?
It is really frustrating having to restart all the time.Any help is appreciated.

---

### Post by thanasvel on 2013-08-11
I found a kind of weird solution ... 
I put a white object in front of the lens and the image appears.
Probably some saturation or some max value makes the driver 
unfreeze. 

I 'll try to install the latest driver for the uvcvideo.
(Which is hard as I have to recompile the kernel)

---

### Post by thanasvel on 2013-08-11
Add this repository and update
[https://launchpad.net/~pj-assis/+archive/testing](https://launchpad.net/~pj-assis/+archive/testing)

That might be a solution

---

