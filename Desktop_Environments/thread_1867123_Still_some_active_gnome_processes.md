---
title: "Still some active gnome processes"
date: 2011-10-22
forum: Desktop Environments
---

### Post by troudobus on 2011-10-22
Hello,

 Sorry for the bother.
I moved, or tried to, from gnome to xfce and it's really pleasant.
However, there are still some active gnome processes, and they can be very very boring.
When I execute ' ps -A | grep gnome ' in the term, I get:
 4069 ?        00:00:00 gnome-keyring-d
 4252 ?        00:00:00 gnome-volume-co
 4261 ?        00:00:00 gnome-power-man
 4265 ?        00:00:00 polkit-gnome-au
 4289 ?        00:00:00 gnome-screensav
 4483 ?        00:00:00 gnome-pty-helpe
 4751 ?        00:00:00 gnome-terminal
 4754 ?        00:00:00 gnome-pty-helpe
 
I know I am not the only one to get bothered with this problem, however I found no solution. Some said it's normal, but obviously not all of it is. For example, frequently the xfce desktop is replaced by the gnome one. There are a lot of other things undergroundly happening too, with some very unpleasant effects. Thus, I want to get totally rid of gnome while using xubuntu. Then, my requests are:

Where do they (gnome processes) come from? 
How can block their auto startup?

Thanks a lot,

---

### Post by gsmanners on 2011-10-22
Have a look in Settings / Session and Startup. That should show you what's up with that.

---

### Post by hhh on 2011-10-22
> **troudobus said:**
> 4069 ?        00:00:00 gnome-keyring-d
gnome-keyring-daemon, saves your passwords through a session, leave it.

> 4252 ?        00:00:00 gnome-volume-co
gnome-volume-control or gnome-volume-control-applet? I'm not seeing it in the list of files for gnome-applets or pulseaudio, so I'm not sure what package it's part of. Maybe you still have gnome-panel installed? Remove it with...```
sudo apt-get purge gnome-panel
```

> 4261 ?        00:00:00 gnome-power-man
gnome-power-manager, remove it...```
sudo apt-get purge gnome-power-manager
```
If you want a power manager, install xfce4-power-manager.

> 4265 ?        00:00:00 polkit-gnome-au
polkit authentication agent, again part of password storage. Leave it.

> 4289 ?        00:00:00 gnome-screensav
gnome-screensaver. Purge it, replace it with xscreensaver if you wish.

> 4483 ?        00:00:00 gnome-pty-helpe
 4751 ?        00:00:00 gnome-terminal
 4754 ?        00:00:00 gnome-pty-helpe
All part of gnome-terminal, I believe. Purge gnome-terminal.
 
> For example, frequently the xfce desktop is replaced by the gnome one.
Purge nautilus.

What steps did you follow to switch from Gnome to Xfce? It seems you missed quite a bit. Have a look at aiyusa's (sorry if I mispelled that, psychocat!) excellent tutorials...

[http://www.psychocats.net/ubuntu/purexfce](http://www.psychocats.net/ubuntu/purexfce)

---

### Post by troudobus on 2011-11-04
Hi,

 Thank you gsmanners and hhh.
@gsmanners: Sadly Settings / Session and Startup isn't very helpful in this case. 
@hhh:
Well, thanks for the explanations.
I installed xubuntu through synaptic.
Actually, I had considered the option of removing packages. But in the beginning I wanted to keep them for safety. Thus, I was looking for a way to just modify the configuration of the appropriate process. 
It is possible, isn't it?

By now, I could drop the gnome packages, but I really want to know who starts these processes and how I can change that (it somehow became a part of my quest to understand linux).

Thanks again for the help gsmanners and hhh.

---

### Post by Jack Brown on 2011-11-04
you could always do a clean install of xubuntu on another partition. (freeing up a partition if you dont have one).

remember to backup your important data first though.


then when you're sure the new install works fine, you can reformat your old partition for more space.

oh yeah, the psychocat link posted by hhh up there gets rid of a lot of gnome stuff, you could try that out first.

Edit: just read the part you mentioned about learning more about linux.  guess you would want to know the reason for some processes running.  good start.  as they say, the more eyes we have in improving open source, the better it becomes.

---

