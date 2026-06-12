---
title: "Screen becomes dark without activating screensaver"
date: 2008-01-30
forum: Desktop Environments
---

### Post by gruhland on 2008-01-30
I use Gutsy with a IBM Thinkpad Z61p and GNOME desktop. After 10 minutes without working on the machine, the screen becomes dark like a screensaver or power management. But I have deactivated the screensaver and the "switch-off screen on inactivity" is set to "never" when the laptop is powered by power supply. I did not find any setting in the bios for the screen. So I don't know where this dark screen comes from.
If I activate the screensaver (let's say after 8 minutes inactivity) it starts to run but after 10 minutes the screen becomes dark too.
Touching on the touchpad reactivates the laptop, the screen becomes light and once can see  for a short moment that the screensaver is working correctly before it stops as it should do. Sometimes only the screen becomes light and the screensaver is running until touching the pad again.

Does someone has an idea which process or driver will initiate the switch-off of the screen?

---

### Post by gruhland on 2008-02-05
DPMS is the cause of it. If you don't want to disable DPMS for fear it may break something else, add this to your xorg.conf:

Section "ServerFlags"
    Option "blank time" "0"
    Option "standby time" "0"
    Option "suspend time" "0"
    Option "off time" "0"
EndSection

---

### Post by tech4 on 2008-03-27
**This post could be related to an Ubuntu bug filed at**: [http://bugzilla.gnome.org/show_bug.cgi?id=342850](http://bugzilla.gnome.org/show_bug.cgi?id=342850) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				I have tried that and I am still having the problem. I have a Dell 8200 and using a ATI Radeon 9800 video card, I am using the drivers downloaded from ATI for the card.  I found a bug report in the problem but that talks about patching a file and applying a patch but it doesn't say what file to patch. I think they are talking about the Gnome-Screensaver.

This where they talk about the patch.
[http://bugzilla.gnome.org/show_bug.cgi?id=342850](http://bugzilla.gnome.org/show_bug.cgi?id=342850)


Any help will be appreciated. 

Lu

---

### Post by gruhland on 2008-03-27
Try to install the graphics driver with Envy:
[http://www.albertomilone.com/nvidia_scripts1.html](http://www.albertomilone.com/nvidia_scripts1.html)
First use the program to remove the old driver and afterwards to build a new one. That could help you maybe.

---

