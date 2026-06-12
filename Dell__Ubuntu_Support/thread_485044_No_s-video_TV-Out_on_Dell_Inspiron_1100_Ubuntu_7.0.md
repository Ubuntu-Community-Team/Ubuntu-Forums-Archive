---
title: "No s-video TV-Out on Dell Inspiron 1100 Ubuntu 7.04"
date: 2007-06-26
forum: Dell  Ubuntu Support
---

### Post by sir_osi on 2007-06-26
Hi, I Hvae Ubuntu 7.04 installed on an old Dell Inspiron 1100. I got everything to work after initial hiccups with wireless and laptop panel video resolution. Now Im looking to get the s-video tv-out feature to work. This is really crucial for me because I do video editing and watch a lot of movies.

Ive looked around the net and tried various suggested xorg.conf modifications, but none work - they either crash X, or dont do anything.

Some relevant  configuration details are as follows:
Total RAM  512 MB.
ndiswrapper -l shows the ialmnt5 Windows driver for onboard video. Ive blacklisted the Ubuntu-native intelfb driver, as part of my attempts to get tv-out working but that hasnt helped.
bcmwl5 : driver installed
        device (14E4:4320) present (alternate driver: bcm43xx)
ialmnt5 : driver installed
        device (8086:2562) present (alternate driver: intelfb)

Ive attached my current xorg.conf, also another version xorg.conf.svideo that crashes X, and finally lspci -vv output.

Id really appreciate any help on getting tv-out working.

Regards

---

### Post by Mguel on 2007-06-27
deleted...

---

### Post by Paul S on 2007-06-27
I don't know anything about your intel video card, so can't answer that, but I have a different broadcom card (dell 1500n) that I can enable with ndiswrapper.  It uses the windows XP driver from dell drivers site fine, but fails on the Vista driver.  So, before you give up, try the other driver available on dell.  Also, there is a site called ftp.dell.com where you can get older versions of drivers for networking and other stuff too.  Keep trying until it works.  If all fails, then you may have to uninstall the ndiswrapper with feisty and install the latest version from ndiswrapper site.  Eventually, something will work.

HTH,

---

### Post by sir_osi on 2007-06-29
Hi Paul S,
My problem is with video out on my TV. Nothing's wrong with mireless or networking.

Regards
Suresh

---

### Post by sk9 on 2007-07-12
Sorry, I am afraid I can't help with your problem but maybe you can assist me.  I have the same laptop and Ubuntu 7.04 shows up on half the screen (the middle part); appears to be resolution issue but don't know how to go about fixing it.  Any suggestion will be appreciated.  Thanks.

---

### Post by vkennedy85 on 2007-12-19
Did updating the xorg.conf file work for you?  I've got the same computer and what to try and get it set up to watch movies.

Thanks.

---

