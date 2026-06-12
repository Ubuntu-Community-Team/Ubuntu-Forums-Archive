---
title: "RT2500 USB Wireless...help needed"
date: 2005-11-27
forum: Desktop Environments
---

### Post by shrink on 2005-11-27
hopefully someone out there can help me with this.

i'm a newbie who's recently moved form that 'other OS' to kubuntu and have found it to be generally straight foward (thank goodness). so now that things are running ok i'd like to get my wireless LAN running again so that i can move the computer back to where it used to be, so...

i've had a go at installing the Ralink USB driver from off their website, following the readme that came with it, and also following some lines from a howto for ubuntu that's at the site serialmonkey. the driver seems to be working (although how do you really tell) as Kwifimanager popped up with the usb card. the problem that i have is that i need to change the setup in the /etc/network/interfaces file manually as the network settings doesn't do this for you, even under root, there's a known bug. i've had a guess at this but it's probably wrong. i'd like to get it set up so that i could change between them when i want to, but with it selecting the wireless at start up.

if anyone can help this would be great, i'll try and do a screen capture to show you if you want.

also maybe there are other places i need to edit that i don't know about??

thanks

---

### Post by daller on 2005-12-01
In "/etc/network/interfaces", change "auto eth0" into "auto rausb0"

That will make the wireless-card connect on bootup...

With the other part, what is your problem?

You connect your wireless with this command:

```
sudo ifdown eth0;sudo ifup rausb0
```

...and to use the wired NIC instead:

```
sudo ifdown rausb0;sudo ifup eth0
```

Good luck!

---

### Post by shrink on 2005-12-05
thanks, i did all that and it's working with kwifi although not perfectly, think i'll need to install the ralink graphical driver also.

thanks again

---

