---
title: "I don't have GUI"
date: 2006-06-18
forum: Desktop Environments
---

### Post by german640 on 2006-06-18
I recently installed Xubuntu in my old Celeron 633 MHz 64 MB of RAM, SiS 630 video card, when I reboot I choose Ubuntu from the Grub, shows various commands like cheking filesystems, starting GNOME display manager, etc. and when is supossed to show the graphic login window, the monitor doesn´t display anything and the power light flashes, and all I can do is press Ctrl+Supr+F2 to enter console mode. I tried the sudo apt-get install xubuntu-desktop command but it says xubuntu-desktop is already installed. ](*,) 

What can I do?

---

### Post by user1397 on 2006-06-18
have you tried ```
startx
``` or ```
sudo dpkg-reconfigure xserver-xorg
```

---

### Post by german640 on 2006-06-18
Some of the messages of startx:

fatal server error:
server is already active for display 0
If this server is no longer running, remove /tmp/.X0-lock and start again.

after a few seconds another messages (there are more)

xinit: unable to connect to Xserver
xauth: error in locking authority file /home/knight/.Xauthority

Then again the command line.

For sudo dpkg-reconfigure xserver-xorg I could see the brand and model of my video card, select it and all the other options leave them as default but I'm in the same problem. Is there anything I must change in the reconfiguration of the xserver?

---

### Post by user1397 on 2006-06-18
[quote=german640]Some of the messages of startx:

fatal server error:
server is already active for display 0
If this server is no longer running, remove /tmp/.X0-lock and start again.

after a few seconds another messages (there are more)

xinit: unable to connect to Xserver
xauth: error in locking authority file /home/knight/.Xauthority

Then again the command line.

For sudo dpkg-reconfigure xserver-xorg I could see the brand and model of my video card, select it and all the other options leave them as default but I'm in the same problem. Is there anything I must change in the reconfiguration of the xserver?[/quote]try the vesa driver for your graphics card.

---

### Post by german640 on 2006-06-18
And how can I install/use the vesa driver and where can I found it?

---

### Post by user1397 on 2006-06-18
you can select it when you use the command ```

sudo dpkg-reconfigure xserver-xorg
```

---

### Post by german640 on 2006-06-18
Nope, it doesn't work either #-o just for know, why the vesa driver?

Maybe I can install another light desktop like fluxbox or icewm?
BUT I don't have internet access on that machine, so I would need to download the desktop to my usb stick and see if I can install it from it :roll:

---

### Post by user1397 on 2006-06-18
[quote=german640]Nope, it doesn't work either #-o just for know, why the vesa driver?

Maybe I can install another light desktop like fluxbox or icewm?
BUT I don't have internet access on that machine, so I would need to download the desktop to my usb stick and see if I can install it from it :roll:[/quote]using the vesa driver just works, for the most part, as I've noticed in these forums that it's recommended a lot.  Judging from the startx error, i'm pretty sure it has to do with the x-server, but i don't know a lot about that, so i can't help you any longer.  sorry!

---

### Post by german640 on 2006-06-18
No problem, snif, I installed Ubuntu (with GNOME) and it worked, but it was TOO slow, so I downloaded Xubuntu but I have this problem. 

I downloaded de xfce in BIN format, maybe installing Ubuntu, then the xfce, and after that removing GNOME, phew! that's a lot of work!
Wait, maybe I can do a server install of Ubuntu and just add the xfce, but how can I find the path to a usb stick?

---

### Post by user1397 on 2006-06-18
[quote=german640]No problem, snif, I installed Ubuntu (with GNOME) and it worked, but it was TOO slow, so I downloaded Xubuntu but I have this problem. 

I downloaded de xfce in BIN format, maybe installing Ubuntu, then the xfce, and after that removing GNOME, phew! that's a lot of work!
Wait, maybe I can do a server install of Ubuntu and just add the xfce, but how can I find the path to a usb stick?[/quote]okay, xfce should not be downloaded in "bin" format, it should be downloaded via the repositories as te packae 'xubuntu-desktop' or by downloading the disc image from here: [http://cdimage.ubuntu.com/xubuntu/releases/dapper/release/](http://cdimage.ubuntu.com/xubuntu/releases/dapper/release/)  that's to do a fresh install.

---

### Post by german640 on 2006-06-19
[QUOTE=erik1397]okay, xfce should not be downloaded in "bin" format, it should be downloaded via the repositories as te packae 'xubuntu-desktop' or by downloading the disc image from here: [http://cdimage.ubuntu.com/xubuntu/releases/dapper/release/](http://cdimage.ubuntu.com/xubuntu/releases/dapper/release/)  that's to do a fresh install.[/QUOTE]

I don't have internet access, so I can't download it via the repositories, and I already downloaded Xubuntu install disc (alternate) and I have this problem with it.

EDIT: I installed Ubuntu and it doesn't work either, so I found that the problem is the monitor, because I changed it and the new monitor worked. So, why Ubuntu and Xubuntu don't work with a specific monitor, because Windows 2000 works very well?

---

### Post by german640 on 2006-06-20
¡Problem solved! =D> 

I did "sudo dpkg-reconfigure xserver-xorg" and I disabled de vbe and ddc options for the monitor, I also changed the vertical synchronization from 50-120 to 50-85 and it worked!

---

