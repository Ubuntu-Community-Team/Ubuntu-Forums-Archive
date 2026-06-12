---
title: "How to set up a VNC server?"
date: 2005-12-12
forum: Desktop Environments
---

### Post by Airjoe on 2005-12-12
Hi.
I use Kubuntu 5.10. I'm wondering how to setup a VNC server.
I did a search, but everything seems to be for Ubuntu, not Kubuntu, and it seems a little different.

I really don't know where to start. I haven't gotten any packages yet.
I need to know how to set up the server, and get it running on port 8000, and how to setup a password.

Thanks in advance.

---

### Post by Ruskie on 2005-12-12
Hi.
Are you sure it is different? I'm not an expert, but I've read extensively on VNC server lately, and it really didn't seem related to the flavor of Linux you are using... all you need is an X server on the machine where the Vnc is running.
Post me the instruction you have found, and maybe we could check them together. Meanwhile I'll go retrieve the info I found in the past weeks.

By the way (I tried that in Ubuntu, but I've seen something similar exists for Kubuntu), some sort of standard desktop sharing already exists in KDE; maybe you could check if it is enough for your needs....

---

### Post by Airjoe on 2005-12-12
Ah, yes, I just found that. It's a desktop sharing thing (Krfb), and it works just as I want. Well... almost. Whenever I try to connect to the computer, I have to click an "allow connection" button from that computer. Anyone know if there's a way to turn that off? I already allowed uninvited users.

[edit]
Nevermind, got it!
Awesome!

---

### Post by Ruskie on 2005-12-12
Here it is. I don't know how many VNC servers do exists, but one of the most popular is RealVNC, or one of its fork, TightVNC (which is a boost of its predecessor, with some advanced features). Both are free, at least to some mostly adequate extent.
I don't know which package you should download because I haven't my Kubuntu box at hand; assuming you have it installed, a server is launched with the script vncserver, I think with a command line like this:

vncserver :1 --httpPort=8000

This will run the daemon Xvnc for the X display 1, listening on port 8000 (note: this is NOT the standard).

The password can be setup or changed with the vncpasswd, which is also called by vncserver the first time it runs.
Let me know if it works. :)

---

### Post by Ruskie on 2005-12-12
Glad to see you've found it. Indeed the "allow connection" thing can be turned off, it is just a matter of finding the option, which I can't do at the moment.
It is not based on port 8000 however... I don't know if it can be changed but I guess so.
If you feel like playing, try the more advanced vncserver as well, as it can be run without you sharing YOUR desktop, but allowing remote users to borrow another desktop on your machine (if that is what you want).

Bye
Marco

---

### Post by Lawless on 2006-01-04
I've got a question..

I dual boot with Win2000.
When I want to work on my Kubuntu installation from another location, I RDP into my win2000 server and reboot. My default OS is Kubuntu so when it comes back up, the server is waiting at the login screen. 
This makes it difficult to VNC (well impossible really) you need to be logged in to make VNC available.

Is there a way to VNC from that screen, or is there a way to have Kubuntu automatically log me in when rebooting or starting up etc?

---

### Post by Lawless on 2006-01-04
I found it, System settings, login manager, convienence, auto login....

---

