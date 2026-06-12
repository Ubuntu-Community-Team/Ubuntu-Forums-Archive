---
title: "Ubuntu 11.10 and Dell SP2208WFP"
date: 2011-10-15
forum: Dell Ubuntu Support (CLOSED)
---

### Post by jedimasterk on 2011-10-15
I own a Dell SP2208WFP monitor but cannot get the webcam working in Ubuntu 11.10.

Error: 

[   11.855871] uvcvideo: Found UVC 1.00 device Monitor Webcam (SP2208WFP) (05a9:2643)
[   11.856206] uvcvideo: UVC non compliance - GET_DEF(PROBE) not supported. Enabling workaround.
[   11.856459] uvcvideo: Failed to query (129) UVC probe control : -32 (exp. 26).
[   11.856462] uvcvideo: Failed to initialize the device (-5).
[   11.856494] usbcore: registered new interface driver uvcvideo

Anyway I can get this working?

---

### Post by Beef Eater on 2012-08-19
Try reloading uvcvideo with the quirks parameter:

```
sudo rmmod uvcvideo
sudo modprobe uvcvideo quirks=2
```

If the above trick does not work after 3-5 attempts, try using 4 or 256 instead of 2, and if that does not work either, try different combinations of the sums of 2, 4 and 256, such as: 6, 258, 260 and 262. This method was proposed in the [Fedora Forums]("http://forums.fedoraforum.org/archive/index.php/t-246787.html").

---

