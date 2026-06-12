---
title: "Panels disappeared after update &amp; power mishap"
date: 2008-06-25
forum: Desktop Environments
---

### Post by demios on 2008-06-25
I'm completely new at this and only had Ubuntu for about a day. installed on the 10 gig recovery partition of my Dell inspiron. so, trying to find the wireless and sound card drivers for that, I decided to run update manager and install everything, which I saw to do somewhere on these forums. I, however had to leave. so two things happened:

1. I set update manager to install the 236ish available updates (should've taken about half an hour)

2. I closed the lid and walked away. I had previously set the power settings to sleep after some 30 mins on battery (which is what it was on), to only turn off the screen when the lid is closed, and to shut down if the battery level reached critical.

so when I got back, the thing had shut down. I tried to start it, red "no battery" light comes on, so I start it plugged in. I boot ubuntu, log in normally, and all I get is a solid background colour. nothing happens when I right click, the only thing I could do was print screen. from that dialogue box I could get to help, which had a link to firefox in it.

vista still boots fine.

sorry if I overcomplicated this and thanks for the help.

---

### Post by sanus|art on 2008-06-25
Do you have desktop effects enabled?

---

### Post by demios on 2008-06-27
I have no idea. I don't think so, unless they are by default.

---

### Post by sanus|art on 2008-06-27
> **demios said:**
> I have no idea. I don't think so, unless they are by default.
They are on with minimal mode by default if your graphic card is supported, try to pass 
```
killall gnome-panel
``` to the terminal - this is supposed to restart all panels that is currently opened.

---

### Post by demios on 2008-06-27
thanks man, I don't think I can get a terminal open, but I'll try again. and I don't think my graphics card is actually supported, it might be using a generic profile or something. I remember I had some problems with that when booting from CD.

---

### Post by sanus|art on 2008-06-28
Try to reinstall the gnome-core and ubuntu-desktop:
```
sudo aptitude reinstall gnome-core ubuntu-desktop gnome-volume-control
``````
killall gnome-panel
``````
sudo /etc/init.d/gdm restart
```Do it trough <Ctrl>+<Alt>+F6

Anyway it is much easier to backup your '/home' and reinstall I think.

---

### Post by demios on 2008-06-28
k, before I try that, I've had some other developments:

I can log on in a GNOME session thing, which was not set to default. That got me a desktop and the panels and stuff, previously I had been logging in in the like Xcontrol or something session. is the GNOME session the 'normal' one, or should Xcontrol or whatever it's called work?

However, I looked up drivers and stuff, and couldn't do anything "sudo" related 'cause I wasn't (and couldn't get) logged in as root.

I dunno, maybe I should just read through the documentation and the forums more hahah. thanks man.

---

### Post by 13blue on 2008-06-28
I just had the same thing (I think) Starting a new thread. Can't figure out how to delete this post.

---

### Post by sanus|art on 2008-06-28
> **demios said:**
> k, before I try that, I've had some other developments:

I can log on in a GNOME session thing, which was not set to default. That got me a desktop and the panels and stuff, previously I had been logging in in the like Xcontrol or something session. is the GNOME session the 'normal' one, or should Xcontrol or whatever it's called work?

However, I looked up drivers and stuff, and couldn't do anything "sudo" related 'cause I wasn't (and couldn't get) logged in as root.

I dunno, maybe I should just read through the documentation and the forums more hahah. thanks man.
Gnome session **IS** supposed to be the default, so you are fine !

---

### Post by demios on 2008-06-28
> **13blue said:**
> I just had the same thing (I think) Starting a new thread. Can't figure out how to delete this post.

k, I figured something out. whenever I tried to install anything or open the restricted drivers thing, it gave me this message telling me to manually run some "dpkg config -a" code (that might not be it exactly). I did that in root, and I think it finished the updating process. 

now everything's running mostly normally (I think), just gotta get those drivers. thanks sanus.

---

