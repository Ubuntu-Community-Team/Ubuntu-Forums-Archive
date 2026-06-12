---
title: "Ubuntu hangs during boot"
date: 2006-07-21
forum: Desktop Environments
---

### Post by ovistanciu on 2006-07-21
Hi!
I'm using Ubuntu 6.06 Dapper on my laptop. I've noticed that if i boot Ubuntu when the network cable is plugged-out, Ubuntu hangs for about 1 min during "Configuring network interfaces...". It's kinda annoying because i'm traveling a lot and my only network connection is at home.

Is there somenthing i can do to reduce this hang time?

---

### Post by Gus Tarballs on 2006-07-21
> **ovistanciu said:**
> Hi!
I'm using Ubuntu 6.06 Dapper on my laptop. I've noticed that if i boot Ubuntu when the network cable is plugged-out, Ubuntu hangs for about 1 min during "Configuring network interfaces...". It's kinda annoying because i'm traveling a lot and my only network connection is at home.

Is there somenthing i can do to reduce this hang time?

You can reduce the timeout for the dhclient.
```

sudo joe /etc/dhcp3/dhclient.conf

```
there should be a commented out line similar to this:
```
#timeout 60;
```
uncomment it and change it to a lower value.
Make sure you don't set the value to low (may need some testing) because your dhcp-server at home needs some time to answer to your laptops request.

---

### Post by ovistanciu on 2006-07-21
it didn't work. i uncommented the line and changed the timeout to 10 and still there was no improvement. it hangs for about 90 sec under "Configuring network interfaces...". am i doing something wrong?

---

### Post by Gus Tarballs on 2006-07-21
You could deactivate the interface in /etc/networking/interfaces. Remove it from the "auto" line. You should keep all other entries (esp. "lo") there. This will require you to start the interface manually (using "ifconfig *interfacename* up") when you need it.

---

### Post by ovistanciu on 2006-07-21
that seems a little drastic, but i'll do it.

anyway, after reading the man page on dhclient.conf it seems a little strange to me that the first solution you suggested didn't work. actually, it isn't the first time when changing a .conf file doesn't do anything. a few days ago i tried to enlarge the subtitles in totem xine. tried it from the menu, set font to 42, nothing happened. then i changed the entry in totem.conf (uncommented the line, etc...) and still nothing happened.

am i missing something? have you got any suggestions?

anyway, thanks for the help you already gave me.

---

### Post by Gus Tarballs on 2006-07-21
I have no idea why changing the config file would not work. Maybe you can try to run the script manually and see where it hangs. 
sudo /etc/init.d/networking restart

---

### Post by neltnerb on 2006-11-01
I think if you just hit CTL-C while it's setting up networking, it aborts.

---

