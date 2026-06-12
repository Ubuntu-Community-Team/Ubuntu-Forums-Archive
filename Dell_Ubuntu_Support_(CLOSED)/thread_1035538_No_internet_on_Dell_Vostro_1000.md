---
title: "No internet on Dell Vostro 1000"
date: 2009-01-09
forum: Dell Ubuntu Support (CLOSED)
---

### Post by Moustaffa on 2009-01-09
Hello,

I use a Dell Vostro 1000, which comes with the following information about network cards:
- Broadcom 440x 10/100 Integrated Controller
- Cisco Systems VPN Adapter
- Dell wireless 1390 WLAN Mini-card

After installing Ubuntu and clicking on the netword icon, there's no wireless network to select. Even if I try to connect manually by giving the network name and ASCII password (afterwards Ubuntu asks for the WEP key, which I insert as well), it keeps asking me to insert the WEP key, over and over, and still no internet.

What to do?

Thanks

---

### Post by epitaph on 2009-01-09
Gah, my bad... I didn't read which NIC it was.

Try doing an lspci to confirm which wireless is in it:

```
lspci | grep Ethernet
```

---

### Post by Moustaffa on 2009-01-09
> **epitaph said:**
> Gah, my bad... I didn't read which NIC it was.

Try doing an lspci to confirm which wireless is in it:

```
lspci | grep Ethernet
```

I'm new to Linux, so I don't know what you mean by "doing an lspci". Where do I have to insert that piece of code? The terminal?

---

### Post by epitaph on 2009-01-09
Yes, you can just copy and paste it into a terminal and then copy and paste the output into the forum post box.

---

### Post by Moustaffa on 2009-01-10
> **epitaph said:**
> Yes, you can just copy and paste it into a terminal and then copy and paste the output into the forum post box.

This is the output I got

08:00.0 Ethernet controller: Broadcom Corporation BCM4401-B0 100Base-TX (rev 02)

So I guess my network card is recognized, however, the driver probably isn't installed, because when I use the command "lsmod", I can't find anything resembling to that lspci output.

I got the "lsmod" command from another forum, where they've put a tutorial online on using commands to install drivers (something about repositories and ndiswrapper).
I'll try the tutorial first, if I encounter some problems, I'll get back to you.

Thanks

---

### Post by epitaph on 2009-01-10
Question: Have you gone to System > Administration > Hardware Drivers and enabled the 3rd party restricted drivers for the Broadcom Wireless in that menu?

---

### Post by Moustaffa on 2009-01-23
> **epitaph said:**
> Question: Have you gone to System > Administration > Hardware Drivers and enabled the 3rd party restricted drivers for the Broadcom Wireless in that menu?

The only thing I can select in that menu is my video driver, so the network driver clearly isn't installed properly and I' ll have to do it with the ndiswrapper.
I found a tutorial on how to do that.
Thanks anyway

---

