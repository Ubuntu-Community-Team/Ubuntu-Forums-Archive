---
title: "Ubuntu doesn't boot anymore"
date: 2006-07-29
forum: Desktop Environments
---

### Post by .Maleficus. on 2006-07-29
Well, I think I did something very bad lol.  I was trying to get my wireless USB adapter working, and I couldn't.  It started with my wireless showing up in Networking, until I followed a guide to install drivers and such.  After I finished doing what the guide said, my wireless card didn't get detected and my eth1 got changed to eth2.  I found that very strange.  I unplugged, and replugged, and restarted, many times and nothing changed.  I decided to take out my ethernet card, that was eth2.  I disabled it before I took it out.  After I took it out, I turned on my computer.  I went through the normal stuff until I got to the loading screen.  It looked like this.

```
Loading essential drivers                          OK
Mounting root file system
Waiting for root file system
```

Then, it went back to what looked like the screen that comes before the loading screen, but it had this on it also.

```
ALERT! /dev/hdc1 does not exist. Dropping to a shell!
```
and
```
/bin/sh: can't access tty; job control turned off
```
It also says I can type Help for a list of commands, but none of the commands seemed to do anything for me.

Thank you for any help!

---

### Post by .Maleficus. on 2006-07-29
*Sigh of relief.*  I got it too boot now.  Still don't have wireless working, but now that it boots I'm a lot happier.

---

### Post by kinematic on 2006-07-29
what was wrong?

---

### Post by jISh on 2006-07-29
Since you have your drivers installed, I'd suggest that you open up your interfaces list, like this:
```
gksudo gedit /etc/network/interfaces
```

Poke around in there, just delete anything regarding eth* and set it all up to work with wlan0 (actually, you should tell us what wireless card you have, and how you installed it, but for this purpose I'll assume it was with ndiswrapper).

This is how my file looks:
```

auto lo
iface lo inet loopback

iface wlan0 inet static
address *erased for paranoid purposes**
netmask 255.255.255.0
gateway *erased for paranoid purposes**
wireless_essid *erased for paranoid purposes**
wireless_mode managed
wireless_channel 6 

auto wlan0

```

---

### Post by .Maleficus. on 2006-07-29
I have a Linksys WUSB11 ver. 2.8.  I followed this guide (I would have used ndiswrapper, but I heard of it after I tried this.) [https://wiki.ubuntu.com/WifiDocs/Device/LinksysWUSB11?highlight=%28WUSB11%29](https://wiki.ubuntu.com/WifiDocs/Device/LinksysWUSB11?highlight=%28WUSB11%29)

I don't know if I would find anything regarding wlan0, because Ubuntu doesn't detect it.

When I plug in my other Linksys wireless card, it detects it and calls it rausb0 or something like that, but when I try to activate it my computer freezes.

---

