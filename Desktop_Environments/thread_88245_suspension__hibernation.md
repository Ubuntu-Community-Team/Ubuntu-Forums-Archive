---
title: "suspension / hibernation"
date: 2005-11-09
forum: Desktop Environments
---

### Post by jimmygoon on 2005-11-09
I would like to know the proper console commands to get my laptop to go into suspend mode. It is a Toshiba Satellite M35X-S161. I was able to "locate hibernate" and find:

/etc/acpi/hibernate.py

and I executed it as root... It looked almost exactly like how GNOME did it, but when it came back out of hibernation it would go through the percentage of pages loaded and every 10 percent(s) or so it would spew out a few lines with the word error in it and then move on ... and repeat. It eventually got to 100% but I fear that some day I'm gonna put it into suspend mode (aka hibernation for me) and I'm not gonna be able to wake it back up properly.

Can someone instruct me. I might note that Gnome (using the menus) is able to suspend 100% perfectly. BTW: I ask this because I'm using XFCE4 now rather than GNOME.

Gracias

---

### Post by Mizzou_Engineer on 2005-11-10
You're doing better than I have. I had to compile swsusp2 into the kernel to get hibernation to work. 

I had problems before with KDE/Gnome and hibernation, that was caused by me suspending Gnome with kdm as the display manager. If you run XFCE, why not set your defualt display manager to xdm instead of gdm?

---

### Post by etc on 2005-11-10
I'm using XFCE also, and I'd like to know how you can hibernate, without recompiling the kernel with suspend2 support.
Also suspend to ram would be nice

---

### Post by jimmygoon on 2005-11-10
[QUOTE=Mizzou_Engineer]You're doing better than I have. I had to compile swsusp2 into the kernel to get hibernation to work. 

I had problems before with KDE/Gnome and hibernation, that was caused by me suspending Gnome with kdm as the display manager. If you run XFCE, why not set your defualt display manager to xdm instead of gdm?[/QUOTE]


:O :O can you tell me how to do that. Its so annoying that I know that gnome crap is running in the background. I would love to get rid of it ;)

btw: The hibernate thing was just a glitch... all I had to do was exec /etc/acpi/hibernate.sh ... the first time was a fluke

---

I hope I didn't just do something I'm gonna regret. I "sudo apt-get install xdm" and it came up with a guide asking which graphical login manager to use and I choose xdm... hope that was the right thing to do. either way... I got another pc. 

OOPS!!! WRONG. I did that and rebooted and it blinked on and off 2.. 3 times? and then kicked me back to the first (tty1) terminal. so... I wound up doing a "sudo apt-get remove xdm" and "sudo dpkg-reconfigure gdm" or something very similair to that. Everytime I think I know enough to do something.... lol

---

### Post by etc on 2005-11-10
I'm pretty sure xdm is insecure, correct me if I'm wrong.
You should use gdm or kdm depending on your setup.
edit: i didnt read the edit

---

### Post by rytmisk on 2005-11-18
Anyone have any idea why this is impossible in icewm? It reboots fine, but the moment it is finished it shuts down the laptop... Annoying to say the least! Nothing is as fast as icewm and still usable in my experience. As it is now I will have to settle for xfce.

And another thing: How do I avoid providing sudo password? Ie run as regular user which works perfectly well from both kde and gnomes powerapplets.
Best regards
Ketil

---

