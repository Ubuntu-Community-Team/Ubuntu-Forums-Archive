---
title: "Gnome 3 All Gone Ugly"
date: 2011-06-07
forum: Desktop Environments
---

### Post by Khakilang on 2011-06-07
I did a clean install of Ubuntu 11.04 with Unity and Gnome classic. Later I install Gnome 3 and Gnome shell with instruction from Ubuntu Geek. All the download seem fine but after the installation everything turn ugly from Unity to Gnome classic. The shutdown command is missing from the menu and the network show disconnected which is actually connected. I attached a screen shot. Is there anyway to make it better? Thank to anyone who reply!

[ATTACH]194452[/ATTACH]

---

### Post by ojdon on 2011-06-07
Have you done these two commands yet?

> sudo apt-get remove gnome-accessibility-themes

sudo apt-get install gnome-themes-standard

Then install gnome-tweak-tool using:
> sudo apt-get install gnome-tweak-tool

To run gnome-tweak-tool simply open up the ALT+F2 run command box and type in &#8220;gnome-tweak-tool&#8221;  once the application appears click on &#8220;Interface&#8221; on the left hand-side menu in the application. From here select the first drop-down box labelled &#8220;Gtk+ Theme&#8221; make sure &#8220;Adwaita&#8221; is selected, same goes for the &#8220;Cursor Theme&#8221; drop-down box. That should fix any theme issues.


^Taken from [here]("http://www.ollie-reardon.co.uk/create-a-linux-tablet-distribution/").

---

### Post by nothingspecial on 2011-06-07
> **Khakilang said:**
>  The shutdown command is missing from the menu 

[ATTACH]194452[/ATTACH]

Click your username on the top right then press the alt key.

The suspend option will change to power off.

---

### Post by Khakilang on 2011-06-09
Thanks! I have try and it did improve. Thanks again guys!

---

### Post by hakermania on 2011-06-09
> **Khakilang said:**
> Thanks! I have try and it did improve. Thanks again guys!

Mark the thread as solved please


Gnome 3 looks nice ;)

---

### Post by beelzebufo on 2011-06-11
not solved, I can't seem to figure out how to get rid of this absolutely hideous windows classic look that appears when I go to gnome 3, I have played with the tweak tool, I have played with the themes settings in the appearance tab, everything, and I can't seem to figure it out, a lot of the time I change the settings and nothing happens, I don't get it.. any extra help would be awesome, I upgraded from 10.10 with the updater and then installed gnome 3 from the terminal, it installed just fine, but, yeah totally ugly in only certain situations threw in some screenshots of what I am talking about, my theme should be set to a dark gray for the window color and rounded buttons

nevermind, I can't get anything to work with gnome 3 just gonna stick with unity

---

