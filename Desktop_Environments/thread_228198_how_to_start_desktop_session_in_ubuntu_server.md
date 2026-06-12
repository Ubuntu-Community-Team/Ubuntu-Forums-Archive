---
title: "how to start desktop session in ubuntu server"
date: 2006-08-02
forum: Desktop Environments
---

### Post by Mia_tech on 2006-08-02
I just installed ubuntu server and also installed "ubuntu-desktop"
after dwonloading all pakages rebooted, and I've looked around trying to find the command to get the x session started

any help will be appreciated

Thanks

---

### Post by siplus on 2006-08-02
I remember when I first started using linux a few years ago, just before the last enormous desktop-usability push, and some distros that I tried didn't boot up into graphical mode by default

If i remember right, you can do one of two things: type 'startx' when you want to start the GUI, or change the default init level so that it boots into graphical mode like the normal desktop version. I remember in redhat/fedora graphical mode is init 5, but I know some distros use different numbering systems

---

### Post by Mia_tech on 2006-08-03
yeah I've already tried startx, was my first choice, but ubuntu does not recognize the command, I'll try the second choice, I just thought there may be a specific command build in to ubuntu to satrt x
thanks

---

### Post by Mia_tech on 2006-08-03
actually I reinstalled ubuntu-desktop from cd, again and now startx
command tries to initialize the x session, but Im getting an error mssg "no /home/username/.xsession" file.

any ideas
checked the /etc/X11/xorg.conf, and it seems to recognising the video card, atleast it shows there.

---

### Post by harisund on 2006-08-03
Did you try ```
sudo /etc/init.d/gdm start
```

---

### Post by ExMachina on 2006-08-03
I use xubuntu-desktop myself
and it auto turns on which i like

---

