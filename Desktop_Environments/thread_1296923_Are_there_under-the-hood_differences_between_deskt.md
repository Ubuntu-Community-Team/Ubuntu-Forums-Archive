---
title: "Are there under-the-hood differences between desktop and UNR"
date: 2009-10-21
forum: Desktop Environments
---

### Post by leandromartinez98 on 2009-10-21
I would like to know if, appart from the appearance, there are actual
kernel optimization for the Atom processor in the Ubuntu Netbook Remix,
particularly Karmic. I'm not interested in the Moblin Remix. 

Also, is there a simple and easty way to uninstall the Remix interface?
(I know how to disable it, but I had bugs with that before, so I would
like to uninstall it). This is the point, if the only difference is the
interface, I would install the standard desktop on my netbook and tweak
the interface to my taste.

Thanks.

---

### Post by leandromartinez98 on 2009-10-21
From here:

[https://launchpad.net/netbook-remix](https://launchpad.net/netbook-remix)

It seems that there are no under-the-hood differences. Correct?

---

### Post by snowpine on 2009-10-21
Hi there,

1. Ubuntu Netbook Remix is not "optimized" for the Atom processor. For that, you want the LPIA (low power intel architecture) port: [http://cdimage.ubuntu.com/ports/releases/9.04/release/](http://cdimage.ubuntu.com/ports/releases/9.04/release/)
2. However, I do not personally recommend LPIA due to the annoyance of obtaining LPIA versions of many apps. "Regular" i386 has worked perfectly for me on my Asus eee and Dell Mini 9.
3. You should be able to install the "standard" Ubuntu desktop and settings with the terminal command "sudo apt-get install ubuntu-desktop".

---

### Post by leandromartinez98 on 2009-10-21
Thank you, that has been my impression. I have installed the
standard ubuntu desktop. It is perfect, I just wandered if 
an Atom-optimization could improve battery life, boot times, etc, 
and then it would be worthwhile to install the NBR.

---

### Post by aeon.flux on 2010-04-19
> **snowpine said:**
> 3. You should be able to install the "standard" Ubuntu desktop and settings with the terminal command "sudo apt-get install ubuntu-desktop".

can i install netbook remix interface on normal pc (notebook) ? where can i find the commands?

---

### Post by snowpine on 2010-04-19
> **aeon.flux said:**
> can i install netbook remix interface on normal pc (notebook) ? where can i find the commands?

I haven't personally tried it (I dislike the netbook interface) but this should work:

```
sudo apt-get install ubuntu-netbook-remix
```

---

### Post by aeon.flux on 2010-04-19
can i use both (netbook and pc) interfaces after install?

---

### Post by snowpine on 2010-04-19
> **aeon.flux said:**
> can i use both (netbook and pc) interfaces after install?

I don't know. You could with 9.04 (System, Preferences, Switch Desktop Mode), but I think they removed that feature from 9.10.

---

### Post by aeon.flux on 2010-04-19
oops! i can't switch back to simple gnome and sudo apt-get remove ubuntu-netbook-remix didn't do any thing :D i'm going to install kubuntu-desktop and hope that KDE will work correctly ; )

---

### Post by aeon.flux on 2010-04-20
i searched in synaptic package manager for netbook remix and removed all packages were installed and i have plain gnome again :shock:

---

