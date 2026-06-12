---
title: "network icons disappear from Gnome Panel"
date: 2009-12-18
forum: Desktop Environments
---

### Post by n4pgw on 2009-12-18
I don't know what happened.  I added a few things to my Gnome Panel and now I have lost my network icons.  

I did this on two computers and both have lost their network icons.  ON the desktop, it is not much of a problem as it is a wired network, but the laptop had the networks in the home changed from auto to manual so it would connect to the device nearest me instead of the one I am further from.

On the desktop, the icon is just missing, not that there were any options.  But the lap top says to click on the symbol to connect to the network, but it is not there so I cannot connect.  

I did have the HP printer symbol, the network symbol , the battery symbol and the speaker symbol in one applet called notification area 2.28.0 copyright 2002 Red Hat.  The only thing missing is the networking icon.  The space it was in is there, but the icon is missing.

Thank you.
Buck

---

### Post by EricDrijv on 2009-12-18
Maybe installing networkmanager applet?
 *sudo apt*-*get install network-manager*

---

### Post by n4pgw on 2009-12-18
```
*sudo apt*-*get install network-manager*
```
I tried that but to no avail.  It said latest version was already installed -- on the desktop.  The script won't work on the laptop as I cannot make the connection.Thanks
Buck

---

### Post by Yvan300 on 2009-12-18
Try removing and adding back the notification applet.

---

### Post by EricDrijv on 2009-12-18
Try pressing alt+f2 and typing **nm-applet --sm-disable**. This should start the applet and let you connect

---

### Post by n4pgw on 2009-12-19
Eric,

I did what you said on both computers.  At first, nothing seemed to have happened, but when I tried moving the icons on the panel, the whole panel went blank and then came back.  I also got two error messages (duplicates) that I normally only get when I boot:  > The panel encountered a problem while loading "OAFIID:GNOME_TSClientApplet".
Do you want to delete the applet from your configuration?

Don't Delete -- Delete

I chose "Don't Delete" on both. The icons came up and all is well (on the desktop computer.)

I then rebooted the laptop.  It came up normally without the error messages this time, and has four icons in the bunch: HP, a phantom volume control (does nothing), a battery, and a working volume control.  Still no network.

Since the error messages are connected with this applet, or whatever is in it, I may have chosen on the laptop "Delete" on some occassion.  

Be advised that I have no network connection on the laptop so deleting and reinstalling from the repositories is not possible at this time.  I haven't tried it yet, but I can probably get on the net by using the wired Ethernet connection.

Thank you, 

Buck

---

### Post by EricDrijv on 2009-12-19
Ah, you wrote: error messages (duplicates) that I normally only get when I boot
You'll probably need to fix the Tsclient to fix your problem
[https://bugs.launchpad.net/ubuntu/+source/tsclient/+bug/399436](https://bugs.launchpad.net/ubuntu/+source/tsclient/+bug/399436)

new tsclient packages
i386
 [http://packages.debian.org/sid/i386/tsclient/download](http://packages.debian.org/sid/i386/tsclient/download)
 AMD64
[http://packages.debian.org/sid/amd64/tsclient/download](http://packages.debian.org/sid/amd64/tsclient/download)

But you need an internet connection for this. Or another computer and a floppy

---

### Post by n4pgw on 2009-12-20
That fixed the error on my desktop, but it took a couple of reboots.

I'll have to hook the laptop to the wired network to see if I can upgrade it.  

I'll work on that today.

Thank you
Buck

---

### Post by n4pgw on 2009-12-21
I managed to get my icon back.  I went to the website above and reinstalled the 'older' version of TSclient. I rebooted, and this time the space for the icon showed up but not the icon so I went to system - Preferences - Network Connections - Wireless  and set the router in my room to automatic.  Once I did that, the network connected and I logged out.  When I logged back into Ubuntu, the icon was where it belonged and all was well.

Thank you to everyone.
Buck

---

### Post by EricDrijv on 2009-12-22
Cool man:popcorn:

---

### Post by n4pgw on 2010-01-03
The problem has not actually gone away.  I discovered it when I was visiting a new location.  However, after I got home again, I discovered that if I change the properties of the top panel (where the icon is) to or from "show hide buttons" the icons correct themselves.  Sometimes I have to make a change more than once, but it seems to work within two changes.

it is still a bug and an annoyance, but it its priority for working on the problem is pretty low now that I have a work-around.

Thank you all for the help and advice.

Buck

---

### Post by mudguts on 2010-01-07
I had a very similar issues on my laptop.
with a bit of hit and miss, trial and error, I discovered the following.

When I would pull out or disengage my PCMCIA Wi-Fi card and reboot, I would get the errors on bootup.

once I plugged it back in or activated the network device then no more errors.

you've already solved it but just in case another laptop owner is curious.

---

### Post by smhnaji on 2010-07-28
Sorry, I couldn't get a clear answer for that

When I saw this link ([http://packages.debian.org/sid/i386/tsclient/download](http://packages.debian.org/sid/i386/tsclient/download)), I downloaded it and executed the following command:

sudo dpkg -i Downloads/tsclient_0.150-4_i386.deb

But after restart (as said in a post), nothing changed.

I had seen that err message about gnome and I had selected "Delete" instead of "Don't Delete" unfortunately.

What exactly should we do to resolve the problem?

---

### Post by smhnaji on 2010-07-29
Solved by RIGHT CLICKING TOP PANNEL --> ADD TO THIS PANEL ---> NOTIFICATION AREA ---> RESTART :D

---

