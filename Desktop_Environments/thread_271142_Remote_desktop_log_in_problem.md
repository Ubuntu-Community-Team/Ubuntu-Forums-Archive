---
title: "Remote desktop log in problem"
date: 2006-10-04
forum: Desktop Environments
---

### Post by fernando_lopes_jr on 2006-10-04
I have installed remote desktop successfully everything is working fine except one thing, every time e reboot the pc I have to log in locally in the pc before I can log in with VNC. Is there a way to get around this? Its really annoying having to log in to the pc so that I can use VNC.

---

### Post by akadruid on 2006-10-04
I had the exact same problem.  I've got a writeup of the different options but basically there are two options straightforward options:
1. Set your computer to log in automatically (not very safe! but if the machine has no way to log on normally, as in a HTPC or something then it's probably good).
2. Install a difference VNC server to replace the one that comes with Ubuntu (vino) - this gives you a different desktop to the one that see on the monitor though.

If you want both bootup security and control of the monitor's display then you could try figuring out what controls vino's startup - I couldn't find much on vino through a little googling though - or else figure out how to link another vncserver to the monitor display, which is probably documented somewhere online.

The original write up is here:
[http://ubuntu.thedruid.co.uk/Starting-a-VNC-Server-on-startup.php](http://ubuntu.thedruid.co.uk/Starting-a-VNC-Server-on-startup.php)

---

### Post by sefs on 2006-10-04
I have had good results with the vnc4server and NXserver
Vnc4server can be installed from the synaptic software installer.  It allows me to log into the machine while the machine itself sits at the login screen.  

The install guide for vnc4server is here... [http://ubuntuforums.org/showthread.php?t=122402&highlight=resumable+sessions](http://ubuntuforums.org/showthread.php?t=122402&highlight=resumable+sessions)

Keep in mind too that when you use the vnc stuff over the internet that it is i believe unencrypted so anyone can snoop in, so would be wise to run it over SSH.  You'll need
1) to install an ssh server ... theres a guid somewhere on this forum
2) get putty ... it exists for both linux and windows not sure for mac and check out example #3 [http://www.vanemery.com/Linux/VNC/vnc-over-ssh.html](http://www.vanemery.com/Linux/VNC/vnc-over-ssh.html)

If you try out NXServer you dont need putty as this by design works over ssh from the application itself once you have ssh server installed on the machine you are connecting too.

---

