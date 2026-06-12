---
title: "Unity wireless icon - how to change for wired?"
date: 2012-10-20
forum: Desktop Environments
---

### Post by inhumangeek on 2012-10-20
I would really like to get rid of the wireless networking logo. I have a wired network connection!

In 11.04 I managed to get a wired networking logo (two arrows) but cannot seem to get them back now I have upgraded. I'm using Unity at the moment.

Thanks,
Paul

---

### Post by inhumangeek on 2012-10-26
There must be a way! Not everyone uses wireless networking, surely?!

---

### Post by cmcanulty on 2012-10-26
mine automatically shows the wired thingy, try disabling wireless and see if it doesn't change the icon

---

### Post by inhumangeek on 2012-10-26
How do I do that?

---

### Post by cmcanulty on 2012-10-26
When I cl the network icon this is an enable/disable wireless. Or go to system settings-network and turn on airplane mode which means wireless is off.

---

### Post by inhumangeek on 2012-10-27
Thanks for looking at my problem!

I cannot disable wireless from the panel (as it is not enabled in the first place). BTW the wired connection says "Not managed".

When I go to system settings I can turn aeroplane mode on but this seems to have no effect. In the settings box I get two options - wired (unmanaged so I cannot hit "configure") and Network Proxy (which says method - none).

---

### Post by cmcanulty on 2012-10-27
you could try reinstalling network manager

---

### Post by inhumangeek on 2012-10-27
OK I might give that a go... thanks for the help.

---

### Post by flint5 on 2012-10-27
Have you disable wireless on your router?
If this is not the problem, try simple to change you icons theme (try faenza-icon-theme).

---

### Post by inhumangeek on 2012-10-27
My computer has no wireless receiver so I really don't think that will help! 

I think it's a configuration glitch with the network manager - when the PC was first set up I had a few problems (if you are interested see some of my early posts!!).

---

### Post by guntbert on 2012-10-27
"not managed" means that network manager is not responsible for your interface.

I assume you have a DHCP server in your network
You will have to edit /etc/network/interfaces to look like 
```

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
#iface eth0 inet dhcp
```

(lines starting with a # are just comments, the important point is that no configuration for eth0 except 'auto' is stated)
Then restart network manager

---

### Post by flint5 on 2012-10-27
Try this: [http://askubuntu.com/questions/71159/network-manager-says-device-not-managed](http://askubuntu.com/questions/71159/network-manager-says-device-not-managed).
I hope this will help!

---

### Post by inhumangeek on 2012-10-28
Bingo - that's worked. I had to select Auto Ethernet from the network manager and then the wireless symbol changed for the arrows.

I suppose this should really be filed under networking... since the wireless icon appeared only after I installed 11.10, I assumed it was something to do with the desktop environment.

Thanks everyone.

---

