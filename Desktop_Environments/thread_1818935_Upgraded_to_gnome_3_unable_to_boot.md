---
title: "Upgraded to gnome 3 unable to boot"
date: 2011-08-05
forum: Desktop Environments
---

### Post by Pipedreams on 2011-08-05
I recently upgraded to gnome 3 and now it won't boot at all. I figure i can't downgrade back so... any info is much appreciated.

---

### Post by wildmanne39 on 2011-08-05
Hi, here is a link on the most common problems with gnome3.
[http://ubuntuforums.org/showthread.php?t=1742343](http://ubuntuforums.org/showthread.php?t=1742343)
Thank you

---

### Post by Pipedreams on 2011-08-07
I can't get to the login screen, I'm stuck at checking battery state... I've tried to purge ppa and revert backwards but I don't have a connection. I'm thinking about a reinstall but I would have to do it from a usb stick... How would mount and boot from a usb before the internal hd boots up? (thanks for the response btw)

---

### Post by garvinrick4 on 2011-08-07
This could help you boot it now uses lightdm instead of gdm. Try these one at a time until
something works I do not know where you are at. All we are trying to do is see if you can
startx if you still have gdm running, is lightdm running, reconfigure to use lightdm use tab to toggle. If not see if lightdm is installed and lightdm-gtk-greeter (most cases seems lightdm-gtk-greeter)
Will not hurt to try these one at a time and see what happens after each. We want gdm to not run lightdm to say running. 

ctrl/alt/f1
login
startx
sudo stop gdm
sudo start lightdm
sudo dpkg-reconfigure lightdm
sudo apt-get install lightdm
sudo apt-get install lightdm-gtk-greeter
sudo reboot
[COLOR=Red]EDIT: I am sorry I have been hanging around 11.10 and thought you upgraded to 11.10[/COLOR]
##This Does not apply to 11.04 running gdm##

---

### Post by sammiev on 2011-08-07
I had to change my boot up at login to Unity or if you have choices of another gnome version you can do so. After bootup run update and your done, just switch back to gnome3 on reboot. I did 3 laptops this way. GL :)

---

### Post by wildmanne39 on 2011-08-07
Hi,
> How would mount and boot from a usb before the internal hd boots up?
If you go this route watch the screen when you boot to see what key to hit to enter setup, it will be like f12, or delete key something like that in setup change boot order to boot usb first.

Or some computers have a one time boot option, it says boot menu when you start your computer, the key maybe the esc. key to enter the boot menu.

---

### Post by Pipedreams on 2011-08-14
Hey guys sorry i didn't get back I had to go to Kansas. Just got back I'll try the steps and give an update. Thanks for the help guys

---

### Post by Pipedreams on 2011-08-14
> **sammiev said:**
> I had to change my boot up at login to Unity or if you have choices of another gnome version you can do so. After bootup run update and your done, just switch back to gnome3 on reboot. I did 3 laptops this way. GL :)

How would i switch back to unity? Honestly i wanna try gnome 3 once i do get this up and running.

---

### Post by Pipedreams on 2011-08-14
Ok so startx allows me to login as root, but i don't have to option of logging in with my user name. For some strange reason i can't update and my repository wont update either. All in all I won't go back to windows...

---

