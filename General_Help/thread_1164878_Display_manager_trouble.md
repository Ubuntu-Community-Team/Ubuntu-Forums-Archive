---
title: "Display manager trouble"
date: 2009-05-20
forum: General Help
---

### Post by leprotic on 2009-05-20
Hi. I just installed Jaunty (64 Bit) and activated the ATI/AMD driver. Everything was fine but I needed to change the resolution for DVI to HDMI connection. When I tried to open display manager, desktop started to flicker and everythin went incredibly slow.

For the record, I have 2600 XT with 2 GB RAM (for all it matters).

Any help is highly appreciated.

---

### Post by Legace on 2009-05-20
Reboot your PC it and select "recovery mode" in boot-manager (GRUB) and then go for "root shell" option. 
After that just type:
```
sudo apt-get remove xorg-driver-fglrx
```

Now you will need to restore your original settings, so either restore any backed-up copy of file /etc/X11/xorg.conf or run something like:
```
sudo dpkg-reconfigure -phigh xserver-xorg
```

or another one (you will have to answer a few simple questions)
```
sudo dpkg-reconfigure xserver-xorg
```


then type
```
exit
```

and select "resume normal boot"

This should get you back to your Ubuntu desktop, but running on default drivers.

Then you can try again :)

---

### Post by leprotic on 2009-05-20
Thanks a lot. But do you have any suggestion for afterwards? Today I'll try the catalyst driver (9.4). Anything else I can try?

---

### Post by Legace on 2009-05-20
If you didn't already, you could also do this, more simple way of accomplishing the above:

```
rm ~/.config/monitorl.xml
```

Then reboot, and try to use the Display manager again..

---

### Post by leprotic on 2009-05-20
Will do, thanks again.

---

