---
title: "Problem with display on Microsoft Virtual Server 2005 R2?"
date: 2006-04-06
forum: Desktop Environments
---

### Post by sebflipper on 2006-04-06
Hi,

I thought I would give Microsoft Virtual Server 2005 R2 ago as they have just released it for free.

I have managed to install Ubuntu 5.10 on it, but when it loads up the login screen the display is garbled in a sort of widescreen mode and you can barley read anything.

I pressed Ctrl+Alt+F1 to drop into the console and using the "**sudo dpkg-reconfigure -phigh xserver-xorg**" command to change the display to the lowest resolution, but its still garbled and unreadable on reboot.

Has any one had any experience installing Ubuntu on Microsoft Virtual Server 2005 R2?

Thanks for any help!

---

### Post by reefland on 2006-04-06
[QUOTE=sebflipper]Hi,
I have managed to install Ubuntu 5.10 on it, but when it loads up the login screen the display is garbled in a sort of widescreen mode and you can barley read anything.
[/QUOTE]

Having exactly the same problem this morning trying to get Kubuntu 5.10 running under Virtual Server 2005 R2.

Tagging along...

---

### Post by sebflipper on 2006-04-06
Found the solution! :D 
[QUOTE=http://vpc.visualwin.com/Notes/Ubuntu.Breezy.5.10.html]Ubuntu Breezy 5.10 Notes

    * If the installer hangs while looking for updates, install without a network card and then add it after the install
    * The DefaultDepth will need to be modified from 24 to 16 bit color:
         Switch to Console mode
               1. Press 'Ctrl + Alt + F1' (F2 - F6)
      and edit the xorg.conf in /etc/X11. 

      #Reboot.[/QUOTE]

---

### Post by reefland on 2006-04-06
Sweet!  worked perfectly.

Thanks.

---

### Post by reefland on 2006-04-06
...  any tips for the sluggish video performance?  Running full screen.  I assume the Microsoft addins for Linux will not help us yet??

---

### Post by sebflipper on 2006-04-06
From what I can see the MS Virtual Machine Additions only provides support for DOS, OS2, and Windows. So no support for *NIX :(

---

### Post by reefland on 2006-04-06
[QUOTE=sebflipper]From what I can see the MS Virtual Machine Additions only provides support for DOS, OS2, and Windows. So no support for *NIX :([/QUOTE]

There is support for *NIX... but nothing Ubuntu specific yet.

[http://blogs.msdn.com/virtual_pc_guy/archive/2006/04/03/566273.aspx](http://blogs.msdn.com/virtual_pc_guy/archive/2006/04/03/566273.aspx)

---

### Post by j0217995 on 2006-04-12
Anyone been able to perform a "server" install?  Using Dapper Server Flight 6 and can't get past a blank screen.  The boot loader starts and then nothing else happens.  I can boot in recovery mode and get a prompt, but nothing else.
Any thoughts?

---

