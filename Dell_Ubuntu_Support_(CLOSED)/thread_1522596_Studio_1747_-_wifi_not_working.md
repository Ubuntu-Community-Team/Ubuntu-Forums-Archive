---
title: "Studio 1747 - wifi not working"
date: 2010-07-02
forum: Dell Ubuntu Support (CLOSED)
---

### Post by dtrosset on 2010-07-02
Hello,

I installed Ubuntu 10.04 amd64 on a Dell Studio 1747.

During the installation process, when the system was running from the Live CD, the wifi has been working correctly.

Since I restarted and booted from the hard drive, I cannot use it. It is show as "not activated" in the network notification area. I tried to install the proprietary drivers, without success. I removed them, same result.

What could I have done wrong ? It was working during the installation !

Didier

---

### Post by /b/rotard on 2010-07-03
> **dtrosset said:**
> Hello,

I installed Ubuntu 10.04 amd64 on a Dell Studio 1747.

During the installation process, when the system was running from the Live CD, the wifi has been working correctly.

Since I restarted and booted from the hard drive, I cannot use it. It is show as "not activated" in the network notification area. I tried to install the proprietary drivers, without success. I removed them, same result.

What could I have done wrong ? It was working during the installation !

Didier

I had this problem on my inspiron, but just so I can help you better, go to the terminal and type "lspci | grep Network"

---

### Post by dtrosset on 2010-07-04
Hello, here it is: 

```
08:00.0 Network controller: Broadcom Corporation BCM4312 802.11b/g (rev 01)
```

Thanks for your help
Didier

---

### Post by olexiyb on 2010-08-14
I found answer here

[http://game-engine.co.uk/2010/06/ubuntu-10-04-and-dell-studio-xps-16-wireless-problems/](http://game-engine.co.uk/2010/06/ubuntu-10-04-and-dell-studio-xps-16-wireless-problems/)

First, unload it temporarily with: 

> sudo rmmod dell_laptop

The various components should un-screw themselves right away. To make the change permanent:

> cd /etc/modprobe.d/
sudo nano blacklist-custom

Copy this into the text document:

> # /etc/modprobe.d/blacklist-custom
# Custom blacklist file so I don’t mess with any of the files that come with
# the module-init-tools package.
blacklist dell_laptop

---

