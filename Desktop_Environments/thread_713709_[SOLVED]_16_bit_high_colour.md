---
title: "[SOLVED] 16 bit high colour"
date: 2008-02-14
forum: Desktop Environments
---

### Post by chips24 on 2008-02-14
how do you change to display settings to 16 bit high colour and 32 bit true colour, i installed a game that uses those settings but dosnt work because the settings are on somthing else, how do you change that?:confused:

---

### Post by hyper_ch on 2008-02-14
Edit your xserver config.

```

sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.old
gksu gedit /etc/X11/xorg.conf

```

---

### Post by Rossross on 2008-02-14
Nm ...  :)

---

### Post by chips24 on 2008-02-14
> **hyper_ch said:**
> Edit your xserver config.

```

sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.old
gksu gedit /etc/X11/xorg.conf

```

where is all this, im still a beginner with ubuntu.

---

### Post by oedha on 2008-02-14
type those on terminal
go to application - accesories - terminal

---

### Post by jan quark on 2008-02-14
```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.old
```
this line will create a backup copy of the file you want to edit

```
gksu gedit /etc/X11/xorg.conf
```

gksu or gksudo give you superuser permission to a graphical applciation

gedit   is an text editor

and /etc/X11/xorg.conf   is the path to the file

xorg.conf is a X Window System server configuration file
it stores important configurations, i.e. graphics, or input devices and many more

---

### Post by chips24 on 2008-02-14
> **jan quark said:**
> ```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.old
```
this line will create a backup copy of the file you want to edit

```
gksu gedit /etc/X11/xorg.conf
```

gksu or gksudo give you superuser permission to a graphical applciation

gedit   is an text editor

and /etc/X11/xorg.conf   is the path to the file

xorg.conf is a X Window System server configuration file
it stores important configurations, i.e. graphics, or input devices and many more

thanks for the detaild information, that helps a little more.

---

### Post by chips24 on 2008-02-15
sudo: cp: - no such file or directory.

---

### Post by chips24 on 2008-02-15
i cant find what im looking for.

---

### Post by chrispche on 2008-02-15
cd /etc/X11 (enter)
sudo nano xorg.conf (enter)

Find you video and res settings and change them, it's quite straight forward.

Then in nano txt editor.

ctrl o to save
ctrl x to exit.

Reboot
ctrl alt del

Hope that helps. If so please thank me, I want one of those.

Oh and the maximum you can go is 24bit which your game will accept.

---

### Post by chips24 on 2008-02-15
i cant find it in the text.

---

### Post by chrispche on 2008-02-17
Post up your xorg.conf file lets have a look.

---

### Post by chips24 on 2008-02-17
I can't, i have no wireless or ethernet connection on ubuntu, just very rarely.

---

### Post by chips24 on 2008-03-03
can some one help me set my desktop to 16 bit high colour?

---

### Post by chips24 on 2008-03-03
still need help

---

### Post by ahaslam on 2008-03-03
```
gksudo gedit /etc/X11/xorg.conf
```
Go to the 'screen' section & change the default depth to 16, ensuring the appropriate depth & modes within the subsection. 
Example:
```
Section "Screen"
    Identifier     "Screen0"
    Device         "Videocard0"
    Monitor        "Monitor0"
    DefaultDepth    16
    SubSection     "Display"
        Depth       16
        Modes      "1280x1024" "1024x768" "800x600"
    EndSubSection
EndSection
```
The effect will be apparent after restarting Xorg.

---

