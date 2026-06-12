---
title: "New To Ubuntu and need Advice"
date: 2010-12-24
forum: Colorado Team - US
---

### Post by tgaston34 on 2010-12-24
Hi all, 

I live in Northern Colorado and I have just started using Ubuntu on my Gateway Laptop and I have to old desktop going to waist in my basement and I want to use them for my Mom who lives 20 miles away from me who wants a computer for Internet surfing and email and My sister who lives in Nebraska about 2 hours from me. I am looking for a program that will allow me to connect remotely to their computers if they run into problems and I can do updates etc without actually having to be there. Can anyone give me any advice. PS neither one of them has much computer experience, I have been using windows since I was 9 so Linux is new but I am willing to learn. Also I am wanting to know about new computer builds this is the year I build my new system and I have decided on a AMD Quad core AM3 system with Radeon 5770 1gb card for video and 500gb Western Digital HD, as well as MSI or Asus for my motherboard. I would like to have the following when I am done, AMD Quad Core 3.0 or Higher, 4gb of DDR3, 2x 500gb hd, 1gb ATI Radeon GDDR5 card and it will be used as the family desktop/file server...:p

---

### Post by squenson on 2010-12-24
If they have Windows, you can install realvnc on their machines and then access them via Remote Desktop.

---

### Post by cipherboy_loc on 2010-12-24
Look into VNC. I use it to remotely administer my Grandma's computer (even though she lives only 45m away). There are ports of VNC to all platforms (Windows, Linux, Mac, etc), along with the clients. The only issue with this is you will have to open up their router to forward the VNC port (usually 5900) to external hosts. And they they will have to accept your log in. I have a script for Windows that launches VNC, and then opens up Firefox (I can change that to Internet Explorer) to display their Public IP Address. BTW, do they use Windows or Ubuntu/Linux?



Cipherboy

---

### Post by tgaston34 on 2010-12-24
I am sorry I didn't explain myself better this is my fault, I am planning to install Ubuntu if I can on both systems since they just want the basic which should work for them for now till they learn more. So windows will not be used on any of the systems. Thanks again.

---

### Post by pricetech on 2010-12-24
VNC is inherently insecure and I wouldn't use it outside a LAN.

If they're using Linux, which sounds like what you plan to set them up with if I understand your post, then SSH is your answer.

If you need a GUI, which you probably will, I recommend NX from nomachine dot com.

You will have to set up port forwarding in their routers so you can access them from the Internet and you might want to modify the port SSH uses, though some would scoff at the "security through obscurity" aspect of that.

A Dynamic DNS provider can help with giving you an URL to point to such as "mom dot whatever dot com" or "sister dot whatever dot com" so you don't have to concern yourself with their current IP.  I'm using DynDNS for this, but there are others.

I'd solicit the help of a tech savvy and trusted friend for testing purposes so you can make sure it works before you leave their homes after setting it up.

---

### Post by tgaston34 on 2010-12-24
Ok so how do I connect to another Ubuntu system with SSH? I found a tutorial on how to install SSH on Ubuntu and connect from a windows machine, but this doesn't help for what I am trying to do.

---

### Post by cipherboy_loc on 2010-12-24
> **pricetech said:**
> VNC is inherently insecure and I wouldn't use it outside a LAN.


Granted, but if you don't leave VNC running all the time, and only turn it on when you need it, it become more secure; you cannot crack a remote service without it running. Also, you can set it up 1) to prompt you for a password to connect, 2) to prompt the host of the server (your Mother/Sister/etc) to accept your connection and 3) to have it only allow one connection at a time. On your way out of administering their system, you can close VNC, thus cutting off others from accessing it. 


If the OP does not need to see the graphical interface, I would go with PriceTech's solution of SSH (preferably using public keys), because SSH is inherently more secure than VNC, and, with the right setup, will stop attempts to crack the system. 


Sorry if the first part seems more like a flame, but VNC is only a hazard when it is running; if you don't have it autostart on boot, no-one can connect.



Cipherboy

---

### Post by cipherboy_loc on 2010-12-26
---SERVER SETUP---
For the VNC server we will be using X11VNC simply because it is the easiest to setup for forwarding an existing X session.

NOTE: Make sure you are logged as the person who will be needing assistance.

To install open a terminal (Applications -> Accessories -> Terminal) and copy+paste/type:

```
sudo apt-get install -y x11vnc vnc4server
```and enter your password (for sudo). This will install the X11VNC and VNC4server packages. VNC4server is needed because X11VNC does not provide a vncpasswd utility which is needed to secure the system. Now we start securing the system.

```

mkdir -p ~/.vnc
vncpasswd ~/.vnc/passwd

```Note, the vncpasswd password must be less than or equal to 8 characters in length.

This will prompt you for a password and then store an encrypted form of it in ~/.vnc/passwd (if you want to see the encrypted form: cat ~/.vnc/passwd).

We have installed the VNC server and ran the basic setup. The next step is to create a launcher for X11VNC that will:
1) Stop any currently running sessions.
2) Tell you what port X11VNC is running on,
3) Tell you what the Public IP Address of that computer is.

To do this, in the terminal type (Actually, read on past this group of commands and come back so that you know what this does):

```

mkdir ~/.tech
cd ~/.tech
cat > vnc-launcher << _EOF

```What we are doing is:

With the first command creating a folder that is hidden (hence the . before the word tech).
The second command moves into the hidden tech directory.
But the third command is a bit harder to explain. Cat is a utility to view plaintext documents. But with advanced re-direction, we can turn it into something that will take what ever you type/paste and save it in the file. Paste the following bit of code into the terminal (it should give you a > as a prompt). Then press the enter key once (to give us a new line), and then type '_EOF' without the quotes.

```

#!/bin/bash

## A help script to start X11 for remote assistance.
## Copyright (C) 2010 Cipherboy_LOC (of the Ubuntu Forums).
## Licensed under the GNU General Public License version 3.

## Kill all other instances of the X11VNC server to ensure that you will always get port 5900.
pkill x11vnc

## Start the server and print out the display that the server is on...
x11vnc -nap -bg -many -rfbauth ~/.vnc/passwd -desktop "VNC ${USER}@${HOSTNAME}" -ncache 2>&1 | grep -i 'PORT='

## Tell the user to give the Public IP Address to the person who will be helping them.
echo -e 'Please give this number to the tech guy:'

## Print out the number:
curl -s http://checkip.dyndns.org/ | grep -o "[[:digit:].]\+"

## Pause before exiting.
sleep 50

```The next thing to do is to (from the terminal) give the hidden tech folder better permissions (to prevent others from running this bit of code (could be a security threat).

```

chmod 754 ~/.tech/ -R
chmod +x ~/.tech/vnc-launch

```The last thing left to do is to create a desktop icon. Remember that use of cat as a one time editor? Lets do that again:

```

cat > ~/Desktop/vnclauncher.desktop << _EOF

```Paste the following block of code into the prompt (again > should be the prompt), then hit the enter key once, and then type '_EOF' again without the quotes.

```

#!/usr/bin/env xdg-open                                                        

[Desktop Entry]
Name=Tech Support
Comment=Allow your Tech Support guy to remotely help you.
TryExec=gnome-terminal
Exec=gnome-terminal -e "bash /home/*/.tech/vnc-launch"
Icon=utilities-terminal
Type=Application
OnlyShowIn=GNOME;

```When clicked, GNOME-Terminal will open and print something like the following:

> 
PORT=5900
Please give this number to the tech guy:
xxx.xxx.xxx.xxx
The only thing that is left for you to do is forward the 5900 port from the router, but that is not something that I can walk you through (due to the differences in routers).


---CLIENT SETUP---

The client setup is simple now that the server is set up. You need to install a VNC viewer:

```

sudo apt-get install vinagre -y

```will install the default GNOME VNC viewer.

---HOWTO CONNECT THE TWO COMPUTERS---
When the person with the VNC server needs help, get them to click on the desktop icon and tell you the "magic number" (their Public IP Address). Start vinagre (Applications -> Internet -> Remote Desktop Viewer), and click the connect button. In the box that comes up, it should look something like the following, except with their PublIc IP Address instead of 'X's:

[ATTACH]179378[/ATTACH]

If you have any questions, please post them here or in another thread,
Cipherboy

---

### Post by majorpay on 2011-05-03
And coming in super-late to the thread to offer some 13th hour advice:
 
TeamViewer
 
I use it for everyone and it has the advantage that I can access it from anywhere.  And best of all?  It's free for non-commercial usage.

---

### Post by Mel Shepherd on 2011-11-17
I'm across the border in Nebraska. I see there is no help team coming from Nebraska. We're always behind on matters, except football. I'm still a newbie with Ubuntu, but more so Ubuntu Forums. 

I'm needing help on an upgrade that was performed. It seems when you upgrade Ubuntu Studio 10.04, to 11.10, you can't log in to Ubuntu desktop with your previous password. I was able to log into XFCE, but I want to get back to a different desktop experience.  So, from within XFCE, I upgraded my desktop to Kubuntu KDE, hoping to eventually get to 4.7.2.  However, even though I selected KDM for my desktop, I can't get to that desktop. Only XFCE.  

How do I solve this problem?  Please help. I accept emails as well as responses in this forum. [email]goodshepherd@nctc.net[/email]

---

### Post by Njall on 2011-11-20
Mel,

   Welcome to our humble Ubuntu Forums Help Desk nook.  Personally I prefer to get my Ubuntu help through [Ubuntu Forums]("http://ubuntuforums.org/") or through the Ubuntu Colorado Local Community mailing list, a.k.a. [CoLoCo]("https://lists.ubuntu.com/mailman/listinfo/ubuntu-us-co").  I have never had to actually ask a question on the Ubuntu Forums.  Some else asked it and I only had to find the question and thereafter the answer.  However, figuring out how someone framed their question can be really daunting.  Another word for daunting in this case is tiring.

  Your post actually meandered a bit.  I think your real question is, "How do I set KDE to be my desktop?"  I entered "change desktop KDE" in the Ubuntu Forums Search box and got [this link]("http://ubuntuforums.org/showthread.php?t=1882259&highlight=change+desktop+KDE") on the second page.  Is this link helpful?

  I'd welcome you to [CoLoCo]("https://lists.ubuntu.com/mailman/listinfo/ubuntu-us-co"), though were I you, I'd keep an electric prod nearby since many (most?) of CoLoCo's active members live in or around Boulder.  Being in Nebraska I suspect an electric prod is easy to come by for you.  ;)

- Nelson

---

