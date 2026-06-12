---
title: "IPX Gaming on Ubuntu Help"
date: 2011-03-19
forum: Gaming &amp; Leisure
---

### Post by Gadgetguy96 on 2011-03-19
Hey, there

I like to play IPX games with Ubuntu since windows 7 no longer supports it.

I want to set up my IPX profile on startup with the terminal on boot-up but I can't find any good help on it.

Here is what I have to do:

I already installed IPX

apt-get install ipx


and every time I want to start it I have to add the profile and  run this in the terminal

sudo modprobe ipx

sudo ipx_interface add -p wlan0 802.2

Thanks for any and all help :)

---

### Post by mips on 2011-03-19
Holy cow, have not touched IPX in over 10yrs so I'm at a loss, have a look at the links below.

[http://forum.winehq.org/viewtopic.php?p=52463&sid=60f90c1899eaefec00762bde28c8fc16](http://forum.winehq.org/viewtopic.php?p=52463&sid=60f90c1899eaefec00762bde28c8fc16)
[http://tldp.org/HOWTO/IPX-HOWTO.html](http://tldp.org/HOWTO/IPX-HOWTO.html)

Have you tried it using a wired connection?

---

### Post by Gadgetguy96 on 2011-03-19
Thanks for the help.

I got it running I was just wondering how to make it start up at boot up with its terminal commands.

---

### Post by Gadgetguy96 on 2011-03-22
Anyone know how to make terminal commands run on start up?

---

### Post by DuckHook on 2011-03-29
As a fellow N00b, I'm not sure how much help I can be. However, I am starting to implement bash scripts in my own startups due to DPMS issues. Search the Ubuntu Howtos for the bash script tutorial. It also tells you where to place and how to configure scripts to run with each login. Sorry advice is so thin, but I'm just learning myself.

---

### Post by perspectoff on 2011-03-29
> **Gadgetguy96 said:**
> Anyone know how to make terminal commands run on start up?

1) You can add the command as a crontab event (crontab -e)
2) You can use gnome-schedule (if using Ubuntu with Gnome)
3) You can autostart a program at bootup (my favourite):

Any program (or script) can be made to Autostart at bootup by creating a symbolic link to that program (or script) in the ~/.config/autostart folder.

For example, to start Firefox at bootup, create a symbolic link:

sudo ln -s /usr/bin/firefox ~/.config/autostart


More info:

Ubuntuguide:
[http://ubuntuguide.org/wiki/Ubuntu:Maverick#Autostart_a_program_at_bootup](http://ubuntuguide.org/wiki/Ubuntu:Maverick#Autostart_a_program_at_bootup)

Kubuntuguide:
[http://www.kubuntuguide.info/index.php/Maverick#Autostart_a_program_at_bootup](http://www.kubuntuguide.info/index.php/Maverick#Autostart_a_program_at_bootup)

---

### Post by Gadgetguy96 on 2011-05-02
I tried making a .sh file in my documents folder with this code:

#!/bin/bash   

sudo chmod sudo modprobe ipx

sudo chmod sudo ipx_interface add -p wlan0 802.2


 and I tried making a symbolic link but nothing happend.

What am I doing wrong?

---

