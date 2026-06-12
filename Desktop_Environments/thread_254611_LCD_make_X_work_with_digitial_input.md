---
title: "LCD: make X work with digitial input"
date: 2006-09-10
forum: Desktop Environments
---

### Post by monkey86 on 2006-09-10
I installed nvidia-glx drivers. I believe 3d acceleration is working propery since glxgears increased from 100fps(nv driver) to 2700fps(nvidia driver).

When I shut down the X server all I got was a black screen. I thought maybe I had to reboot ( acoording to the driver instructions, sometimes you might. ) I still got a black screen. I tried changing my monitor to analog input and it worked. ( I saw the login, instead of a blank black screen )

**How do I get digital input to work** again? ( It used to use that before the drivers were installed )

I attached my /etc/X11/xorg.conf file. Do you need any configs or log files?

---

### Post by tuxinvader on 2006-09-10
In the Nvidia device section, try adding:

   Option "ConnectedMonitor" "DFP"

You could read /usr/share/doc/nvidia-glx/README.txt.gz for more info

---

