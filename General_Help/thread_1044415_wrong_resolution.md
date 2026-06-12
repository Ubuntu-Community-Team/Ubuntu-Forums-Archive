---
title: "wrong resolution"
date: 2009-01-19
forum: General Help
---

### Post by vegetali on 2009-01-19
I have a 13inches laptop. At work I have a 19inches monitor, so today I attached the monitor to the laptop and used "screenresolution" to manage the double monitor. It really worked ok. BUT... Then I shut down, disconnected the monitor cable, and started again (so my laptop is not connected to any additional monitor now). Each time I start I get in the gnome interface, but there is no panel (I guess the panel is out of the screen). If I launch screen-resolution and click "detect monitor" and then I click "apply", the panel is back. But -both before and after this detect+apply trick- the view on the screen is deformed (very large. for instance I appear fatter than I am in my pictures). In the screen resolution, I can choose between three options, and all of them feature this deformed view.

Please help, this is my only tool for working, and cannot stick with such a deformed view for long. I am thinking about reinstalling the system from zero; but I would like to solve the problem, so that I can work with the larger monitor everyday.

thanks

---

### Post by vegetali on 2009-02-02
Bump

---

### Post by zwygart on 2009-02-02
You may need to reconfigure xorg

Check in "man xorg.conf" and "man xorg". The command looks like xorgconfigure

Also make a backup of your actual xorg
#cp /etc/X11/xorg.conf /etc/X11/xorg.conf.bak

You may add manually a entrie in the mentionned xorg file, but this is not easy and may produce difficulties later.

---

