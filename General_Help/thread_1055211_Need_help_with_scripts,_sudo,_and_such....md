---
title: "Need help with scripts, sudo, and such..."
date: 2009-01-30
forum: General Help
---

### Post by motoDrizzt on 2009-01-30
Well, in reality I need help finding a way to force Ubuntu do what I want it to do :-D

Hi all, I'm new, this is my first real install of a Linux PC.
I've just finished setting up the entire system I wanted, now I'd need help with a few script and boot related things.

The PC is connected via WIFI at my home network, where there is a BSD file server exposing an NFS share, and I want to use a Wiimote instead of the mouse.
Before I forget: how can I contact linuxwireless's guys? I've built a custom driver for my Wi-Fi usb stick simply by adding it's device ID to the driver, and it works quite well...


Ok, I was saying...the system works ok, but the boot it's a little bit clumsy.
I need that, at boot, the system connect to the Wifi network, mount the NFS share from the server and run the sw for using the Wiimote as a mouse.
Problem are:
At boot the Wifi doesn't connect because its WEP key it's in the keyring file, which it seems cannot be accessed from the system if I don't do it manually before (using Edit Connection from the network manager.) So the NFS mount don't happen, because there is no network.

And the Wiimote subsystem needs sudo to works, so i still manually need to launch it everytime.

Can someone be so kind to tell me what to do to solve the situation? I was thinking of a script doing all the work at the user login, but honestly I dunno where to start :-\

---

### Post by cmnorton on 2009-01-30
Under Applications --> Accessories --> Passwords and Encryption Keys is the place to set up a default key. Your Network Manager should be able to start up automatically. Edit: This link might help you.

[http://ubuntuforums.org/showthread.php?t=1044388&page=3](http://ubuntuforums.org/showthread.php?t=1044388&page=3)

End Edit:

As to having other things go on automatically, you can write a script and modify (as root) /etc/init.d/rc.local so that your script is called. As long as your script is protected chmod 755 your-script, it can be in your /home space and be called. You'll need to read that file (rc.local) and experiment with something benign, like 

#!/bin/bash

touch /home/whoeveryouare/test

and then see if test's date changes when you log in. Of course, you would test the script first without its being called from rc.local.

As to forcing Ubuntu, that's what OSs are for. You don't have to force them as much as ask them to do stuff. Usually they will do it, and only not, when we've written crazy code -- I've written plenty -- that does not work right.

---

