---
title: "Outrageous login time"
date: 2005-12-20
forum: Desktop Environments
---

### Post by psYchotic on 2005-12-20
Hello to you, fellow Ubuntu users =)

I am new to Ubuntu, in fact, I'm new to linux. So I will first say that this forum has been a **great** resource to me. That's why I'm posting this.

When I booted into Ubuntu, typed my username and password and hit enter, I would have to wait about 5 minutes before Gnome would finally load. I've been rebooting so many times and waiting for so long that I almost considered wiping Ubuntu off of my hard disk.
Anyway, as I said, it took me about 5 minutes to login : a brown screen would appear, I could move the cursor around, I could even open a virtual shell (ctrl+alt+F1). I found out that it's my networking options that has been causing this. To login normally again, I had to do the following :
[list][*]First go to System -> Administration -> Networking and deactivate the connection I'm using
[*]Then open a terminal and ```
sudo iwconfig wlan0 essid [my essid]
sudo iwconfig wlan0 enc s:[my ASCII wep key]
sudo dhclient wlan0

**Note** that perhaps you don't have a wireless network card, or maybe you have more. Change according to your system.
```[/list]

Now comes my question : how come configuring my wireless network connection using System -> Administration -> Networking makes Gnome hang on login? A detail I omitted is that I have to use ndiswrapper to load the drivers.
Thanks in advance

---

### Post by tlc on 2005-12-20
I had the BSOD (brown screen of death) too. Search - it's a common problem. There are various solutions depending on the exact cause, but I fixed it by editing my xorg.conf file and replacing the "nv" driver with "vesa" - this allowed me to at least get a desktop up. I then installed the latest nvidia driver and changed my xorg.conf to use it - "nvidia" instead of "vesa"

```
sudo nano /etc/X11/xorg.conf
``` to edit the file.

---

### Post by psYchotic on 2005-12-20
Yeah, I noticed the many threads about this issue, but none seem to apply to my situation, which is why I posted.
But I'll look into installing the ATI drivers later (I don't really need them yet).

---

