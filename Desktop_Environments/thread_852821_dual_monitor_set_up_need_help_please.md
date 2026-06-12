---
title: "dual monitor set up need help please"
date: 2008-07-08
forum: Desktop Environments
---

### Post by suicidejack on 2008-07-08
I have nvidia-settings installed and it works sort of.  I've got it to display a twin screen; however, when it displays the twin screen on the external monitor it cuts off the bottom and the right side early.  Also, how do you get each monitor to display different workspaces?  I've looked around but I can't seem to find anything that solved this problem.

I'm running Ubuntu Hardy on a Dell Latitude D820 with a resolution of 1920 x 1200 and a nvidia graphics card (the screen looks correct on this).  My external screen has a resolution of 1690 x 1050 (the screen cuts off on this monitor).

Any help is appreciated and if you need more info let me know!

---

### Post by Buzzdee on 2008-07-08
To my knowledge, you have 2 options with the NVidia drivers:
1) Clone the desktop: You will clone the image from the main monitor (your laptop) to the external screen, thus cutting off the edges, since your laptop has a higher resolution. I think resizing is disabled because it would mess up the picture quality.
2) Extend the desktop: Make one screen the primary and position the other desktop next to it. They still are one workspace, but bigger.

I'm soon going to set up a similar case in my room (laptop 1680x1050, monitor 1280x1024) and will make more experiences with that. If I find any further information, I'll let you know. 

Bastian

---

### Post by Nycthbris on 2008-07-08
My friend is having a similar problem with the screen getting cut off when using an external display. I believe the card is a nvidia quadro 1400. I used nvidia-settings so that the only output is the external (@ 1680 x 1050). The external display (Samsung Sync Master 216B I think) itself can be used to change the horizontal size of the image but not the vertical size. Also the auto-config option on the display does not fix the problem. I'm pretty sure the refresh rates are set correctly also, but the problem still persists.

---

### Post by bimmerd00d on 2008-07-08
as far as i know, you're going to have to use the nvidia-settings applet to change your resolution on the fly.  I have a D820 with the 1920x1200 and Nvidia Quadro 120m (Geforce Go 7400) and this is how i do it.  I use the Twinview function.  I just change it when i get to work, and then shut it down and it uses the saved xorg.conf to default back to the laptop display when i go home.

---

### Post by jsdraven on 2008-07-24
Sys{ 8.04 (Hardy)
2.6.24-19-generic Kernel
GNOME 2.22.3}

i used the add/remove applications to install the NVIDIA X Server Settings.

Before going any further I did something that may be frown on by people who know what they are doing lol. first backup the current xorg.conf file.

then for the not so good part:
```

cd /etc/X11
sudo chmod 777 xorg.conf
```

reason for this is that the file located where it is and being owned by root prevents it from being edited by an out side source like the NVIDIA settings application.

now with done you will be able to go in and select what you want to do like configure it be a TwinView (enlarged work area where you can pass windows between and be able to enlarge that that one monitor) or Separate X Screen (2 Separate work areas with separate work space selections).

after setting and saving your settings you will want to hold CTRL+ALT+Backspace to stop your xorg. you will stay in your current instance but in terminal mode. now to restart your GUI
```
startx
```

I hope this helps you with what your looking for.

In addition I'm looking for some help from whom ever can,

I have setup Separate X Screen using NVIDIA 7900 GT KO in SLi.

My secondary monitor is an oldy. The NVIDIA X Server Settings is not allowing the selection of the Screen Resolutions i know it can handle.

---

