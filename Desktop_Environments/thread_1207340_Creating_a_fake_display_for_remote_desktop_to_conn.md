---
title: "Creating a fake display for remote desktop to connect to"
date: 2009-07-08
forum: Desktop Environments
---

### Post by Imunalia on 2009-07-08
Ok, so I have a problem that I cannot figure out and I just got my system running agian soooo without any further ado....

I want to connect to my media center via VNC on my mobile device so that I can add/check on torrents when I am out of town. The problem however is that the media center is connected to my 1920x1080 TV. This presents a large problem when sending the desktop to my mobile. It can do it, but I go grey by the time it gets there. Basically what I want to do is be able to have a virtual display that I can put my torrent window in so that when I connect to the remote desktop it doesnt take a month of sundays. 680x480 is the target as that is the resolution of my mobile. I have tried tightvnc with disaterous results (Read First Line) Thank god for backups :D.

Currently I running Jaunty with a newer ATI Card. If you need the spec's I can post them. I have a spare monitor that I could connect if that would work but a soft solution would be best. I imagine it just has something to do with configuring X properly but that has also ended in disaster previously....(Aside: Mother Beeping ATI DRIVERS HOW I WANT TO KILL YOU ALLL) Any help would be great and I promise to reward you with hero cookies.

BONUS QUESTION:

Speaking of the ATI drivers I will give my first born to the person who can get mine to run properly on my box. I dont care what ugly hacks it takes and I will allow you to VNC onto my box instead of posting directions.

Jeff

---

### Post by Janeway on 2009-07-08
Hi,

I am currently trying to establish a connection from my laptop to my media centre when I'm away. I also had speed problems with a remote gnome session and XNest. But I think you can change the resolution there. If you have high speed internet you might try that.

I got a valid connection with SSH and X11 Forwarding. That does not need that much data and I can open each graphical app with something like "ssh your_user@your_ip/domain , password and then command. That works fine.

Regards
Janeway

---

