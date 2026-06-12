---
title: "Login window on wrong screen"
date: 2018-12-27
forum: Desktop Environments
---

### Post by hamburgerjungejr on 2018-12-27
Hi,

I'm running Ubuntu 18.10 on my Laptop. At Home I'm having three monitors (1 built-in and 2 external over DisplayPort chained)
After booting the Laptop the login window is displayed on the built-in display and the other monitors are in wrong order

Display Setup:
[[IMG]https://thumbs.picr.de/34684754ji.jpg[/IMG]]("https://show.picr.de/34684754ji.png.html")

I've already copied my monitors.xml to /var/lib/gdm3/.config
Also if I lock the PC after loggin in the monitor settings are correct.

How can I move the login window to the center monitor?

---

### Post by #&amp;thj^% on 2018-12-27
This takes a couple of tries sometimes.


This works for me:

Go into Settings >>> Devices >>> Displays and configure your monitors the way you want them for your login screen.
Copy your user's monitors.xml file into your home folder for gdm user.

To copy the monitors.xml file, open a terminal and run the following:
```

sudo cp ~/.config/monitors.xml ~gdm/.config/monitors.xml
sudo chown gdm:gdm ~gdm/.config/monitors.xml
```

I also had to edit "/etc/gdm3/custom.conf" un-comment
```
WaylandEnable=false
```

---

### Post by hamburgerjungejr on 2018-12-27
Very interesting.
Now it works.
I've already read about disabling Wayland, but the custom.conf file was missing, so I created one and inserted the deamon section and WaylendEnable=False, but no difference after reboot.
Now I've checked again and the file was filled with the default configuration, where Wayland was enabled.

---

