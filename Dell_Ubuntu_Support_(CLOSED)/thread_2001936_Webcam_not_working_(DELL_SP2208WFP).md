---
title: "Webcam not working (DELL SP2208WFP)"
date: 2012-06-11
forum: Dell Ubuntu Support (CLOSED)
---

### Post by Cez on 2012-06-11
Just in case anyone is looking, this worked for me!

from:
[http://zim.ma/9g8u4]("http://zim.ma/9g8u4")

Re: Webcam not working (Dell SP2208WFP)
Try from terminal
rmmod uvcvideo
modprobe uvcvideo
dmseg

Repeat these (<5) until the camera initialises okay..

---

### Post by Beef Eater on 2012-08-19
This method used to work for me in prior installations of Ubuntu. However, in my Ubuntu 12.04 64-bit installation "modprobe uvcvideo" is largely unsuccessful. If it fails to initialize the webcam in 5-8 attempts, it fails consistently afterwards until I reboot my computer.

The solution is to use the quirks parameter that tweaks the webcam probing method. The parameter takes values of 2, 4 and 256 and the combinations of the sums of these values (e.g. 6, 258, 260 and 262). In my particular case, the value of 262 worked perfectly and now my webcam initializes properly from the first attempt in 100% of the cases:

<CODE>sudo rmmod uvcvideo
sudo modprobe uvcvideo quirks=262</CODE>

This method was first proposed in the [Fedora Forums]("http://forums.fedoraforum.org/archive/index.php/t-246787.html").

---

