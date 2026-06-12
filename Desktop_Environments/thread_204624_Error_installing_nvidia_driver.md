---
title: "Error installing nvidia driver"
date: 2006-06-27
forum: Desktop Environments
---

### Post by lnxquestions on 2006-06-27
Hi guys ....
After installing nvidia-glx and running this command to enable it : "sudo nvidia-glx-config enable" i got this error ```
Error: your X configuration has been altered.
This script cannot proceed automatically. If you believe that this
not correct, you can update the md5sum entry executing the following
command:
md5sum /etc/X11/xorg.conf | sudo tee /var/lib/x11/xorg.conf.md5sum
otherwise edit manually /etc/X11/xorg.conf to change the Driver section
from nv to nvidia.

```

What should i do now ?

---

### Post by Dr. Nick on 2006-06-27
Are you still in a GUI?

If so then open a terminal and run

gksudo gedit /etc/X11/xorg.conf

If your in a command line then run

sudo nano /etc/X11/xorg.conf


Once open look under the device section for driver and change "nv" to "nvidia"

Then save and reboot/ or use ctrl+alt+backspace to logoff and back on

If you get a error and a blue screen at boot after doing this, then just do it in reverse to get back to a gui

---

### Post by lnxquestions on 2006-06-27
Hi Dr .. I found it but the drive is not nv but vesa .
Anyway i will try to change it with nvidia and hope that will work .

---

### Post by Dr. Nick on 2006-06-27
aslong as your card is nvidia you should be ok.

Being set to vesa is just fine to, vesa is just a generic driver that works with almost anything. Being set to vesa triggered your origional error. The sudo nvidia-glx-config enable script was assuming it would find "nv" but didnt so it just gave you a error instead of guessing what to change and screwing it up for you.

---

### Post by lnxquestions on 2006-06-27
Thanks alot Dr. Nick everything worked great and i saw the nvidia logo befor gnome started ....

---

