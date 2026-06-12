---
title: "Remote Desktop from windows to ubuntu using ssh and tunnels"
date: 2006-08-08
forum: Desktop Environments
---

### Post by SmokeyMcDave on 2006-08-08
Hi all,

I connect to my windows XP machine at work from my linux machine.  To do this I establish an ssh connection through putty and then remote desktop to localhost:3390.  

I was just trying to figure out how to get it to work from work to my home desktop.  I would use vnc but it is very slow and doesn't display everything properly.  

Any help with this issue would be greatly appreciated.  Thanks in advance.

Also I forgot to mention that I set up tunneling in the putty session using 3390 for the local port and workip:3389 for the destination.       

Smokey McDave

---

### Post by Phixion on 2006-08-08
download openssh-server on your Ubuntu box (sudo apt-get install openssh-server)

Then open port 22 on your router (if you have one) and connect to your Ubuntu Box's external IP address.

Not sure if this is what you needed... o_O It'll ssh to your Linux box but I'm not sure about the remote Desktop part :/

---

### Post by harisund on 2006-08-08
Wait, let me try and understand what you are trying to do:

You have a Windows machine at work, and a Linux machine at home and want to access them from one another.

From your Linux box you access your Windows box using RDP. Why the port forwarding? From what machine/port you are forwarding to what machine/port?

---

### Post by Tehas on 2006-08-08
Look for FreeNX for your Linux machine and then NXClient from No Machines for your Windows box.  The NXClient is free from the No Machines company.

FreeNX will allow you to have a remote desktop session from your host machine (Linux) and have it displayed on your client machine (Windows).  It's similar to VNC but it much quicker and responsive.

The NX connection uses SSH.  **I'd recommend that you not use the standard port 22 though**, move SSH to a different port if you're opening it through your firewall.  Keeping to the standard port number invites attacks from the outside!

Here's an article on how to set up FreeNX on Ubuntu.  [http://www.linux.com/article.pl?sid=06/05/05/1718238]("http://www.linux.com/article.pl?sid=06/05/05/1718238")

The article recommends that you keep the original SSH key pair that comes with the product but I opted to generate my own key pair just to be safe / paranoid.

---

