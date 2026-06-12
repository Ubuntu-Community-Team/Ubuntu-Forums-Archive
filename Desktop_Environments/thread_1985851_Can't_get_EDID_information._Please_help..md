---
title: "Can't get EDID information. Please help."
date: 2012-05-23
forum: Desktop Environments
---

### Post by PeterTaps on 2012-05-23
Folks,

I am running Ubuntu 11.10 64-bit on a clean system. The system has nVidia GeForce GTS 450 HDMI card in it.

When I run "sudo read-edid" on the machine, I get an error that the monitor and video combo does not support DDC1 and DDC2 transfers.

I am wondering if there is any other way to automate getting EDID information.

Although nvidia-settings has an option to fetch EDID information, it can happen only from the GUI. For my needs, I am looking for a console based mechanism so that I can automate the process.

Thank you in advance for your help.

Regards,
Peter

---

### Post by papibe on 2012-05-24
Hi PeterTaps.

I think you meant get-edid right? The package is called read-edid, but you used like this:
```
sudo get-edid | parse-edid
```
Is that how you're using it?

Regards.

---

### Post by PeterTaps on 2012-05-24
Sorry. That was a typo. I was using "get-edid." 

Regards,
Peter

---

### Post by markbl on 2012-05-24
I recently created a little utility [edid-rw]("https://github.com/bulletmark/edid-rw") to read and write edid data.

I used it to fix the edid in one of my monitors so I could use the nouveau xorg driver which, unlike nvidia, can not use the xorg.conf custom/ignore edid options.

---

### Post by PeterTaps on 2012-05-25
Thank you very much for your help. Your code helped me find my problem.

Regards,
Peter

---

