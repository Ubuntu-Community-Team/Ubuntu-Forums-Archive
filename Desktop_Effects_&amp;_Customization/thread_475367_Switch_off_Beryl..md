---
title: "Switch off Beryl."
date: 2007-06-16
forum: Desktop Effects &amp; Customization
---

### Post by stuart_75 on 2007-06-16
Just changed my video card from ATI to Nvidea, now i just get a white desktop and nothing else. I had Beryl running before without any problems.

How can I switch it off via the recovery console?

Please help, thanks!

---

### Post by zero244 on 2007-06-17
Fixing your situation is not an easy one.
If you didnt install the nvidia drivers. I would put the ATI card back in and try to get into your desktop. Turn beryl off and make Metacity or something your mangager.
Not knowing what your xorg looks like, set the driver as "vesa" shutdown and then put your nvidia card in.

If you did install the nvidia drivers you need to open your xorg.conf and set the driver as "nv"
Then reboot your machine should boot up with basic drivers.

To open your xorg file type this in terminal
gksu gedit /etc/X11/xorg.conf
This command will back up your xorg.
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf_bak
Once you get your screen back do a search and get the info you need to change video cards.
Changing video cards in Ubuntu is a lot like windows except Linux doesnt have a generic vesa mode on the boot menu. You have to set it up manually.

---

### Post by steveneddy on 2007-06-17
Press CTRL+ALT+F1 to get you to a CLI.

```
sudo dpkg -reconfigure xserver-xorg
```

then choose vesa as the video driver, NOT NVIDIA!!

then type in terminal

```
sudo /etc/init.d/gdm restart
```

Go to Synaptic and uninstall the ATI drivers and let it run until finished.

Then while still in Synaptic, select the nvidia drivers. I suggest the nvidia-glx-new and the nvidia-kernal-common


```
sudo dpkg -reconfigure xserver-xorg
```

again, this time choosing the nvidia driver.

---

