---
title: "Xserver Error"
date: 2006-11-15
forum: Desktop Environments
---

### Post by Zeek00 on 2006-11-15
Hey,

I recently did an update to my system. I didn't choose any files that really pretained to the X config. After I updated I went to reboot my computer and I got this error:

> Failed to start the X Server. It is likely that it is not set up correctly. Would you like to view the X Server output to diagnose the problem.

Then it Spits me into a shell. So I type:

`sudo cp /var/backups/xorg/xorg.conf /etc/X11/xorg.conf'

To bring up the configuration I know works. I reboot and get into X-windows. I then open up a shell and type:

`gksu gedit /etc/X11/xorg.conf'

And change the driver name for my video card from "nv" to "nvidia" and I reboot the computer. I get the same problem. Failed to start the X Server with the same message as stated above. So I go through the process of restoring my xorg.conf file from the backups and now I'm back into X.

It worked fine before with "nvidia" as the driver name. I did no updates to my video drivers to my knowledge. So any suggestions would be awesome.

Zeek

---

### Post by taurus on 2006-11-15
Try to reconfigure it again with

```
sudo dpkg-reconfigure -phigh xserver-xorg
```

---

### Post by Zeek00 on 2006-11-17
Thanks, I managed to figure it out.

I downloaded the latest verion of the Nvidia drivers off the Ubuntu update. I then typed:

`gksu gedit /etc/X11/xorg.conf'

And I changed "nv" to "nvidia" as the video card driver name. I'm not sure exactly what caused it. But I do know that the 'v' in 'nvidia' has to be lower case else you get the same problem.

---

### Post by taurus on 2006-11-17
Linux or Unix is case sensitive so upper case is not the same as lower case...

---

### Post by Zeek00 on 2006-11-22
Yeah, I understand its all case sensitive. I was under the impression that because the actual business logo was nVidia that it might use that as the name for the driver.

But thanks for the help!

Zeek

---

