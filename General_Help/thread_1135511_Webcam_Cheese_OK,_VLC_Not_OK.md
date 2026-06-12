---
title: "Webcam: Cheese: OK, VLC: Not OK"
date: 2009-04-24
forum: General Help
---

### Post by imbjr on 2009-04-24
My simple "CIF Single Chip" webcam works happily with Cheese but cannot be coaxed to do so with VLC.

gstreamer-properties indicates that it is indeed supported by video4linux (v4l2) and tests OK too, but VLC will not have it. This is a regression too, as a previous release of Ubuntu handled this - though I cannot recall which.

Any ideas on getting this to work?

---

### Post by RubenK on 2009-05-15
No idea why this is the way it is. I have exactly the same problem. Problem is, it's not something vlc does, at least, vlc is not the only one. My webcam also doesn't work in Mercury messenger and aMsn.

imbjr, can you see whether your webcam sort of works when you select the PVR function in vlc?

---

### Post by imbjr on 2009-05-16
> **RubenK said:**
> No idea why this is the way it is. I have exactly the same problem. Problem is, it's not something vlc does, at least, vlc is not the only one. My webcam also doesn't work in Mercury messenger and aMsn.

imbjr, can you see whether your webcam sort of works when you select the PVR function in vlc?

No luck under PVR either. Cheese is still good.

---

### Post by RubenK on 2009-05-16
Can you post your output of lsmod | grep videodev ? It's probably the gspca driver. As Ubuntu calls it [here](https://help.ubuntu.com/community/Webcam#Intrepid/Updated%20Hardy%20current%20issues%20with%20webcam%20s) 'The mother of all webcam related bugs'. I haven't looked into it deeply yet, but I reckon it'll be solved over time...

---

### Post by imbjr on 2009-05-17
> **RubenK said:**
> Can you post your output of lsmod | grep videodev ? It's probably the gspca driver. As Ubuntu calls it [here](https://help.ubuntu.com/community/Webcam#Intrepid/Updated%20Hardy%20current%20issues%20with%20webcam%20s) 'The mother of all webcam related bugs'. I haven't looked into it deeply yet, but I reckon it'll be solved over time...

Here's the output:

```
videodev               41600  3 gspca_main,tuner,ivtv
v4l1_compat            21764  1 videodev
```

...

Just read:
[https://bugs.edge.launchpad.net/ubuntu/+source/libv4l/+bug/260918](https://bugs.edge.launchpad.net/ubuntu/+source/libv4l/+bug/260918)
and discovered that:

```
LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so vlc
```

fixes my problem.

Cheers.

---

### Post by RubenK on 2009-05-17
You are my hero!!!!! I've now got it working in my messenger client (Mercury) too. And to make things nice and organized and easy. I renamed the mercury file in /usr/bin to mercury_main and created a new file named mercury (there's the big trick) which says: ```
LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so mercury_main
```

THANK YOU!!!! :D

---

### Post by imbjr on 2009-05-17
Marked as solved then!

---

