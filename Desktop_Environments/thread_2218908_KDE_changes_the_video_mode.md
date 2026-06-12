---
title: "KDE changes the video mode"
date: 2014-04-22
forum: Desktop Environments
---

### Post by vitke on 2014-04-22
I have a monitor with a 1440x900 resolution which does not report EDID correctly and a NVIDIA card. I have specified this resolution in a modeline in xorg.conf. When KDM starts, the resolution is as I set it. However, since I upgraded to 14.04, during the KDE startup the resolution changes to 1024x768. During reboot my xorg.conf file is renamed. Thus I'd like to know:

1) What sets the resolution and how can I disable it?
2) What renames xorg.conf and how can I disable it?
3) Is there a preffered way to fix the resolution?

---

### Post by SeijiSensei on 2014-04-22
Are you using the proprietary driver?  If not, try that first.  Install it by running the "Additional Drivers" application in the System section of the Kubuntu menu.  That will also install an application to manage the device called, I believe, the "NVIDIA Control Center."

---

### Post by vitke on 2014-04-23
I am using the proprietary NVIDIA driver 304.117. The 1440x900 resolution is available in the NVIDIA Control Center but whatever I set there is ignored.

---

### Post by vitke on 2014-04-23
I found it. System settings -> Display configuration shows an image of a screen and no text. There are three icons in this image and the third one is for setting the resolution. Something like pressing a non-marked brick on the wall to open a secret passage. I really think ignoring the well-established way to set the resolution is a terrible design. Thanks SeijiSensei.

---

### Post by vitke on 2014-04-23
But something still renames my xorg.conf on reboot.

---

### Post by mörgæs on 2014-04-23
Might be related (I am aware that you are using 304):
[https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers-331/+bug/1293789](https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers-331/+bug/1293789)

---

### Post by vitke on 2014-04-23
nvidia-prime was indeed installed and xorg.conf is renamed by adding the date at the end, just like described in the linked bug report, although not at each X restart but only at system restarts. I removed nvidia-prime, but my xorg.conf is stil renamed at each system restart.

---

### Post by SeijiSensei on 2014-04-23
I don't have an explanation, but you can set the "immutable" bit which should preserve the file. Read "man chattr" for details.

---

### Post by vitke on 2014-04-24
Setting the immutable bit did the job. Thanks!

---

### Post by mörgæs on 2014-04-24
Good, please mark the thread 'solved'.

---

### Post by SeijiSensei on 2014-04-24
Just remember that if you ever need to edit or delete the file, you'll need to turn off the immutable bit.  Even root cannot alter an immutable file.

---

