---
title: "Nvidia Drivers wont activate?????"
date: 2009-01-02
forum: General Help
---

### Post by dtrot55 on 2009-01-02
I just installed Kubuntu 8.10 and a window popped up asking if i wanted to activate my nvidia driver...i clicked activate and nuthing happend...i enabled some desktop effects and now the desktop is lagging like crazy...any ideas????

---

### Post by SuperSonic4 on 2009-01-02
I think it's a bug in kubuntu. If you drop to a terminal (ctrl+alt+f2) and type ```
sudo apt-get install nvidia-glx-177
``` which should install the drivers. Then reset kdm by ```
sudo /etc/init.d/kdm restart
```

---

### Post by gettinoriginal on 2009-01-02
Check here:
System > Admin > Check Hardware Drivers to make sure the driver is activated, then:
System > Preferences > Appearance > Visual Effects should be set to Extra or Custom.

---

### Post by jerome1232 on 2009-01-02
> **dtrot55 said:**
> I just installed Kubuntu 8.10 and a window popped up asking if i wanted to activate my nvidia driver...i clicked activate and nuthing happend...i enabled some desktop effects and now the desktop is lagging like crazy...any ideas????

This happens to me too, If I update the system, reboot, then activate the drivers it works fine. YMMV though.

---

### Post by dtrot55 on 2009-01-02
Apparently the custom desktop stuff i activated messed up my desktop .... won't even load correctly now..so i did a ctrl+alt+f2 at the login and typed in the code above and seeing if that will work

---

### Post by dtrot55 on 2009-01-02
I have multiple monitors and when i go  to the nvidia settings i get 

"You do not appear to be using the NVIDIA X driver. Please edit your X configuration file (just run nvidia xconfig as root) and restart the x server"

Any ideas???

---

### Post by jerome1232 on 2009-01-02
Have you installed the driver yet? If so then run nvidia-xconfig and restart x.

```
sudo nvidia-xconfig
```

If not install the driver first then run nvidia-settings.

---

### Post by dtrot55 on 2009-01-02
i had to go back to ubuntu...i was getting random errors for no reason while in kubuntu...i will def use the code for installing and running the nvidia from the root...thanks for the help again!!!

---

### Post by dtrot55 on 2009-01-03
> **jerome1232 said:**
> Have you installed the driver yet? If so then run nvidia-xconfig and restart x.

```
sudo nvidia-xconfig
```

If not install the driver first then run nvidia-settings.

I did this the first time and it worked...i went back in th second time to tweak some things and im getting that same error again ... and when i go to the terminal to run the code above i get this:

dtrot@Ubuntu:~$ sudo nvidia-xconfig

Using X configuration file: "/etc/X11/xorg.conf".
Backed up file '/etc/X11/xorg.conf' as '/etc/X11/xorg.conf.backup'
New X configuration file written to '/etc/X11/xorg.conf'


It doesnt start up the x server settings anymore ?????

---

### Post by jerome1232 on 2009-01-03
After running nvidia-xconfig, then nvidia-settings should stop complaining about you not using the nvidia driver, (I don't know why nvidia-settings can't do this itself)

To pull up nvidia-settings (where you get to config settings)
```
gksu nvidia-settings
```

---

