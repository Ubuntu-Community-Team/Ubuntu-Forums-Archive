---
title: "cannot set resolution"
date: 2005-01-10
forum: General Help
---

### Post by Panos on 2005-01-10
Hello everyone,

I'm a linux newbie, although I have succefully installed a couple of distros in the past (mostly suse). I must say I am impressed with ubuntu's hardware detection.

I installed the 64 bit version of ubuntu and the nvidia driver with apt-get, but there is no way to set the resolution higher than 1024x768. My video card is a plain Geforce 6800 with 128MB and my monitor is a TFT LG 1715S with 1280x1024 native resolution. I have manually configured the XF86Config-4 file, but to no avail.  The option for 1280x1024 is not available in Gnome's panel no matter what I do.

I have read a few other posts mentioning the same problem, but I haven't fingured out the solution yet.

Any help will be much appreciated.

Thank you.
----------------------------------------------------------------
Ok, I had to enter the exact orizontal and vertical frequencies of my monitor. What I did was to enter manually only the desired resolutions. However, after entering the correct frequencies, gnome autodetected correctly all resolutions.

---

### Post by Wim Sturkenboom on 2005-01-17
What did you modify in the config? Often. it's forgotten to modify the following two lines (which reflect the specs of the monitor):```
HorizSync 28-49
VertRefresh 43-72
```Make sure those lines reflect what your monitor can do.

---

