---
title: "A Screen Resolution Issue."
date: 2010-02-06
forum: Desktop Environments
---

### Post by wbee on 2010-02-06
Hello,

In the past month or two,I have "updated" to the newest kernels.

The one previous to the latest,I would boot up and it would load an incorrect screen resolution. I would hold my computer on button to get to the screen to reboot.I did so(both rebooting and shutting down) and on maybe the third or forth try,it would load the correct resolution. After maybe a week or two of this,it settled down and loaded the correct resolution every time.

I had to go System>Administration>Nvidia X Server Settings for the driver to load and I still do,regardless if the resolution is correct or not.

This morning,(having updated to the newest kernel yesterday)it loaded the incorrect resolution again,and it loaded correctly on the third try. Again,I had to engage the Nvidia driver by the means described above.

Are there settings on the Nvidia screen or shell codes I can use to fix these things?

-----------

Thank you.

---

### Post by wbee on 2010-02-09
bump

---

### Post by dE_logics on 2010-02-09
I think you need to recompile the nvidia kernel.

If you installed them through the repositories - 

dpkg-reconfigure <that package name for nvidia drivers>


If you downloaded from the site, just rerun the binary after stopping X


If this doesn't help...try to reconfigure xserver. After stopping X - 

Xorg -configure

It places the new configuration file somewhere (it will tell, I forgot). copy that file to /etc/X11 with the name Xorg.conf and start/restart X.

---

### Post by wbee on 2010-02-10
dE_logics,

Thank you.

So far,so good.

---

