---
title: "GUI for screen res in KDE"
date: 2006-05-08
forum: Desktop Environments
---

### Post by bbarrons on 2006-05-08
I have been using gnome on dapper 6.06 but my wife and kids really like KDE better so I let them switch when I am not around. ( yeah I know, nice guy) here is the problem. I cant find in KDE where to switch the screen res and refresh rate. IS it usually there and my KDE is just broke? What do I look for? 
thanks
Bill

---

### Post by mips on 2006-05-08
it's under System Settings. Or from the terminal type **kcontrol**

then go Peripherals->Display

---

### Post by bbarrons on 2006-05-08
displays must be broke. There is no selection for displays under kcontrol. That is where I thought it had been before. everything but. no listing under system settings either. I tried: sudo dpkg-reconfigure xserver-xorg but it crashes after  I  get past the section to choose res.

---

### Post by bbarrons on 2006-05-08
yep...broke. did a reboot and lost the gui. I renamed the xorg.conf file and used a previous file and was able to boot to GUI. I have the displays in Gnome and can change them but cant in KDE. looks like it is time for some more research......

---

### Post by mips on 2006-05-08
have you tried **sudo dpkg-reconfigure xserver-xorg** ?

---

### Post by kko1 on 2006-05-08
[QUOTE=mips]have you tried **sudo dpkg-reconfigure xserver-xorg** ?[/QUOTE]

He has, and X is fully functional. ;)

Anyway - in case this helps: I can reach the ordinary display settings two ways.

1. K Menu -> System Settings -> Hardware / Display.
2. Right click on empty desktop, choose "Configure Desktop", choose "Display".

If those aren't reachable, then probably either something is missing from your installation, or something has broken your personal configuration, in which case re-naming the directory ~/.kde (which contains your KDE-settings) to e.g. ~/.kde-old might help, effectively letting the system create a new kde-profile. If you've made complex settings to your KDE, you may not want to simply remove the ~/.kde(-old) -folder, as you can later copy the configuration files to the new from there to the new folder as needed.


You might want to try running "krandrtray", which stands for "KDE Resize and Rotate System Tray App", which will thereafter reside in your ... you probably guessed this ... system tray. :)

HTH.

kko

---

### Post by bbarrons on 2006-05-08
thanks kko. both of those options dont exist in the programs menu. no hardware-display or no display option when configure desktop. krandrtray worked fine and the resolution has been changed to something i can read without my glasses on. :-)
I did rename the .kde folder to kde.old and logged back in. It created a new folder bu that didnt change the options listed. SO, krand gave me what I needed
but something is still missing. not a concern now  that I have an option to do what I need. thanks for the reply.
 Bill

---

### Post by kko1 on 2006-05-09
You're welcome. :) 

kko

---

### Post by aysiu on 2006-05-09
[QUOTE=bbarrons]There is no selection for displays under kcontrol. That is where I thought it had been before.[/QUOTE] Weird.

---

### Post by bbarrons on 2006-05-09
what is really wierd is I can log into gnome and it is there.   I had used xandros for about a year and it was kde based and I always found it in the control center. I should try a reinstall of the kde desktop to see if it repairs it.
Bill

---

### Post by bbarrons on 2006-05-09
reinstalled kde desktop and it is there...... thanks for the push in the right direction 
Bill

---

### Post by kko1 on 2006-05-13
Glad to see that you've solved the issue also on the "System Settings" -side.

Plus, I appreciate when posters follow up their posts telling that (& preferably how) their problem was solved. :)

kko

---

### Post by geoken on 2006-05-18
I have the exact same problem as bbarrons. I'll try re-installing KDE and see if that helps me as well.

---

