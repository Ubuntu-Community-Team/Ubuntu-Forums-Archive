---
title: "Lost panels"
date: 2008-11-20
forum: Desktop Environments
---

### Post by conal on 2008-11-20
Hi Folks

I have just installed Ubuntu 8.10 to a usb stick in the hope that I can take my graphics work with Scribus etc on the road.

Problem is this:

Having installed a bunch of software and rebooted several times I now have no menus or panels. Please let me know how to get them back! using alt-f2 does nothing so I cant even get a terminal!!

Kind Rgards

Conal

---

### Post by basilwatson on 2008-11-20
exactly what has happened to me , though I am using Hardy Heron, an app locked up the system so I had to reboot and no panels on restart ..Alt  F2 doesnt work 

I can get to the failsafe terminal though

How can we sort this out ??  Is it a gconf problem or a graphics card ? (Nividia)


Kind Regards Stephen

---

### Post by frankleeee on 2008-11-20
> **conal said:**
> Hi Folks

I have just installed Ubuntu 8.10 to a usb stick in the hope that I can take my graphics work with Scribus etc on the road.

Problem is this:

Having installed a bunch of software and rebooted several times I now have no menus or panels. Please let me know how to get them back! using alt-f2 does nothing so I cant even get a terminal!!

Kind Rgards

Conal

Right click where you want the panel-new panel then add stuff from add to panel.

---

### Post by basilwatson on 2008-11-20
Sorry we cant , the whole panel thing is gone , all you get is the ususl commands when you click on the desktop , cut paste ,,,change background ,,, and I personally cant log in as root to use synaptic to re load panels 

I seem to remember that you delete the gconf file and reboot but I am not sure ,,,

Iam off googleing in a min.  Ive had a similar problem with XFCE 


Stephen

---

### Post by basilwatson on 2008-11-20
Back in action

In a new session , ctrl alt backspace

failsafe terminal

sudo su  ie make yourself root 


I removed gnome-panels  ( rm gnome-panels ??) I am not sure of the comand as I did it yesterday in an attempt to fix it 


then apt-get install gnome-panels 

log out 

log back in to a gnome session 

bingo panels are there ,,except , trash , mixer and user switcher 

so I used synaptic and reinstalled them 

So up and running as per usual 


Hope this helps 


Stephen

---

### Post by conal on 2008-11-21
Thanks Stephen, I'll try that after work and let you know how i get on!

---

