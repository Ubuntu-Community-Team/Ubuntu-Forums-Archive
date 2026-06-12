---
title: "sudo command hangs"
date: 2006-08-18
forum: Desktop Environments
---

### Post by usererror on 2006-08-18
Background: Just building a box for users to have an internet station, with browsing only.  Network connection will be a linksys card that works!

I went into Network Devices in Gnome, and set the ra0, the linksys card to be the default gateway device.  Now when I reboot the PC it hangs on Configuring Network Devices, and if i press Ctrl + C to abort that it'll boot, but then fails to load Gnome after I logon.

If I press CTRL + ALT + F* i can get a command prompt and logon, but if i try ANY sudo xxx command it just hangs.

Any suggestions?  Thanks :D

---

### Post by fdoving on 2006-08-18
Did you change the hostname?
The hostname in /etc/hostname must be in /etc/hosts and resolv to a IP.

Is the 'lo' interface up?
Run:
```

$ sudo ifconfig

```

is 'lo' listed? 

If not edit /etc/network/interfaces and check that you have:
```

# The loopback network interface
auto lo
iface lo inet loopback

```


- Frode

---

### Post by usererror on 2006-08-21
fdoving,

sorry for the delay.  I just turned off the onboard NIC and am currently formatting the hard drive and reloading everything from scratch.  we'll see what this does.

i didn't change the hostname...how would that cause all the commands to hang?

---

### Post by usererror on 2006-08-21
Damn!

Well I turned off the onboard NIC, reloaded Ubuntu.  Activated the Wifi Card, got an IP in Gnome, works great.

Then I rebooted.  Same thing.  I press CTRL + ALT + F4 to get to a command promt, and i try to run ifconfig or sudo ifconfig and it HANGS again.

Gonna try to boot from the live CD to fix the problem hopefully, so i can try what Frode suggested now.

well, i tried booting to the "safe mode" ubuntu, and even now when i try to run a sudo command it hangs.  suggestions? ](*,)

---

### Post by usererror on 2006-08-21
Well I fixed my problem.

Reloaded, again, from scratch.

went into terminal.

ran the following:

```
iwconfig ra0 essid "Internet"
```

```
sudo vi /etc/network/interfaces
```

added the following line:
```

auto ra0
iface ra0 inet dhcp

```

```
/etc/init.d/networking restart
```

the restart was successful, so i rebooted and it came up perfectly.  i did NOT use the GUI network config tool at all this time.

---

