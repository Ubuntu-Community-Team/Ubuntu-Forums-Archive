---
title: "Graphical login at startup broken"
date: 2005-09-10
forum: Desktop Environments
---

### Post by antimoni on 2005-09-10
I removed some applications with Synaptic and I was not very careful. It seems that I accidently removed something important, because Gnome went little crazy and when I rebooted I did not get graphical login screen but shell.

When I did "startx", X server started but no Gnome. I did "sudo apt-get gnome" and it installed whole Gnome again.

Now when computer starts it still goes to shell login, but after loggin in, I can get to Gnome with "startx". When I want computer to shutdown and do System-Log out there is only "Log Out" option in the panel where there used to be "Reboot" and "Shutdown" options as well.

I want nice graphical login and easy shutdown panel back again! Is there easy way to fix this or is it better to install Hoary again or maybe update to Breezy?

---

### Post by cwaldbieser on 2005-09-10
[QUOTE=antimoni]I removed some applications with Synaptic and I was not very careful. It seems that I accidently removed something important, because Gnome went little crazy and when I rebooted I did not get graphical login screen but shell.

When I did "startx", X server started but no Gnome. I did "sudo apt-get gnome" and it installed whole Gnome again.

Now when computer starts it still goes to shell login, but after loggin in, I can get to Gnome with "startx". When I want computer to shutdown and do System-Log out there is only "Log Out" option in the panel where there used to be "Reboot" and "Shutdown" options as well.

I want nice graphical login and easy shutdown panel back again! Is there easy way to fix this or is it better to install Hoary again or maybe update to Breezy?[/QUOTE]
You probably need to reinstall or reconfigure the Gnome Display Manager (gdm).  This command should tell you if you have it installed:

```
dpkg -l '*gdm*'
``` 
It should have something like "ii" next to it if it was unpacked and installed.

---

### Post by antimoni on 2005-09-10
[QUOTE=cwaldbieser]You probably need to reinstall or reconfigure the Gnome Display Manager (gdm).  This command should tell you if you have it installed:

```
dpkg -l '*gdm*'
``` 
It should have something like "ii" next to it if it was unpacked and installed.[/QUOTE]

Thank you, Cwaldbieser!

Thats it. I had to install gdm. Now login and logout are OK. :grin: 

I have no idea how gdm got uninstalled in the first place. I thought I removed Anjuta and Glade. Apparently I have to be more careful with synaptic.

---

### Post by rafakl on 2005-09-10
Same thing happened to me, but not uninstallig packages, but installig new packages.

I didt read when apt-get said what packages will it remove and uninstalled my nvidia-glx driver and gnome without notice.  [-X 

I solved it with:

sudo apt-get install ubuntu-desktop
 ](*,)

---

