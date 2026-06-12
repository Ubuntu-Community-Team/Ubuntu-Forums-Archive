---
title: "Update broke higher video resolutions on M1330N"
date: 2009-08-30
forum: Dell Ubuntu Support (CLOSED)
---

### Post by ABluz on 2009-08-30
The update last week (including kernel -59 patch) broke the video (NVidiia 8400 series) on a Dell XPS M1330N with Ubuntu 8.04 pre-installed.  Now it will only run in 800x600 or 640x480.  Full resolution (1280x800?) isn't available.  How do I get it back?

TIA

---

### Post by RedRat on 2009-08-30
> **ABluz said:**
> The update last week (including kernel -59 patch) broke the video (NVidiia 8400 series) on a Dell XPS M1330N with Ubuntu 8.04 pre-installed.  Now it will only run in 800x600 or 640x480.  Full resolution (1280x800?) isn't available.  How do I get it back?

TIA

It sounds as if you have lost your nVidia driver. I suggest that you download envyNG and use that to download the proper nVidia driver. Also download nvidia-settings from Synaptic. It was there in 8.04 but I don't know if it is there for 9.04. 

after envyNG installs the driver use nvidia-settings to set your resolution. You MUST use it with sudo:

```

sudo nvidia-settings
```

or 
```

gksudo nvidia-settings
```

If you do not run it with the sudo command, it will not save your setting to .conf file.

---

### Post by ABluz on 2009-08-31
Thank you.  I was beginning to decide that the NVidia driver wasn't working, even though it seems to be in the kernel modules.  Why a minor level patch breaks it I don't understand, unless I missed something in the latest kernel patch's version.  It will be tonight or tomorrow before I can try this out.  Thanks.

---

### Post by RedRat on 2009-08-31
> **ABluz said:**
> Thank you.  I was beginning to decide that the NVidia driver wasn't working, even though it seems to be in the kernel modules.  Why a minor level patch breaks it I don't understand, unless I missed something in the latest kernel patch's version.  It will be tonight or tomorrow before I can try this out.  Thanks.

As I have blogged here many times, welcome to Ubuntu's perhaps greatest annoyance: The graphics driver Problem!! I have had this happen to me on several occasions since I became an Ubuntu user over a year and half ago. This may or may not help your situation but hope it works for you.

---

### Post by ABluz on 2009-09-01
This works perfectly.  Thank you.

---

