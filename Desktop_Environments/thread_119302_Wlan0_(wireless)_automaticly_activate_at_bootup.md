---
title: "Wlan0 (wireless) automaticly activate at bootup"
date: 2006-01-19
forum: Desktop Environments
---

### Post by dreesie on 2006-01-19
dear all,

today I had my Asus WL-100g wirless pcmcia card working with Linuxant driverloader, finaly wireless again.
Only one thing I don't understand is that everytime, after a boot the wlan0 is deactivated and has to be manually activated, after that it works perfect. does anyone of you know how to do this automaticly?

I'm just a beginner but during the bootup I see first the network beeing started up en after a while the pcmcia slot is activated. Is it maby so that first the  pcmcia slot has to be activated en then the network"things" has to be loaded. anyone knows how to do dat?

Thanks in advance.

---

### Post by Lambert on 2006-01-19
post your /etc/network/interfaces file here. You can xxx out all personal data.

---

### Post by robotgeek on 2006-01-19
You need to add the relevant modules to be loaded at /etc/modules.
The file /etc/network/interfaces should contain the following lines at the minimum. 
```

iface wlan0 inet dhcp
auto wlan0

```

Refer to [https://wiki.ubuntu.com/WiFiHowto](https://wiki.ubuntu.com/WiFiHowto)

---

### Post by dreesie on 2006-01-20
Finally i've got the solution, I found out that the driverloader did activate the pcmcia slot, it did it after the system itself started up the slot, a double startup witch it cannot handle.
I shut down the system activation of the pcmcia and put the driverloader activation higher in the startuplist and it worked.

Thanks for thinking with me.

Dreesie

---

