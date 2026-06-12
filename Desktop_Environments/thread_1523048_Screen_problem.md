---
title: "Screen problem"
date: 2010-07-03
forum: Desktop Environments
---

### Post by Mostafa Rastin on 2010-07-03
Hi,
I have been using Ubunut 8.04 Heron without any problem, later on i have  upgraded the same computer to 9.10 KOla without any problem, last week I have upgraded the same computer to 10.04 Lucid, but I do not get full screen on my monitor, menu bars and panels  are not accessible, only I can use Alt+Tab to open applications and my document files. I think there is some problem with my VGA configuration. I am not able to access system configuration to change the set up. Any body can help me?

---

### Post by luceerose on 2010-07-03
I had the same problem with an old obscure model of taiwanese plasma.
I used a crt monitor for installation then changed the display resolution before plugging into the plasma.
You could try booting onto a command-line via the grub-menu &
```
sudo nano /etc/X11/xorg.conf
```
to edit the display resolution.
Add the following line in the "Screen" Section replacing any previous 'metamode' entries.
```
    Option         "metamodes" "1024x768_75 +0+0"
```
In that example 1024x768_75 means 1024x768 pixels at 75Hz.
Change the 75 to 85 if your monitor supports it.

---

### Post by Mostafa Rastin on 2010-07-04
Thank you for reply.
My computer does not have a xorg.conf file at /etc/X11
How to generate a xorg.conf file?

---

### Post by SmokeyThePanda on 2010-07-05
You can just create one and add the options, I believe. 

As an alternative to the above strategy:

Search online for the vertical refresh, horizontal sync and maximum resolution for your monitor. After obtaining the information, open up your xorg.conf.

```
sudo nano /etc/X11/xorg.conf
```

You need to edit the following to fit your monitor. (Example is from my own xorg.conf)

```
Section "Device"
        Identifier      "Configured Video Device"
EndSection

Section "Monitor"
    Identifier    "Generic Monitor"
    HorizSync     30 - 60
    VertRefresh   60 - 75
EndSection

Section "Screen"
    Identifier    "Default Screen"
    Device        "Configured Video Device"
    Monitor        "Generic Monitor"
    DefaultDepth    16
    SubSection "Display"
        Depth        16
        Modes      "1024x768" "800x600" "640x480"
    EndSubSection
```

Simply add the values you searched up to fit your monitor. This should work to make your resolution bigger, therefore allowing you to see your panels. I hope it helps you. :)

---

