---
title: "Destop Environment for Ubantu server 22.04.01"
date: 2022-10-31
forum: Desktop Environments
---

### Post by rbcc-12 on 2022-10-31
I am in the middle of building a server using Ubantu Server 22.04.01 , I would like to use a Gui for the ease of it.  Is there one I can use ?  How do I install it on the machine where I have Server on?   Can it be done? Can I download it?  Where to Find it ??   Server doesn't have gnome in it?


Also, how do I setup server for wifi and 2 windows 11 machines?  

Thank you,

JTM

---

### Post by QIII on 2022-10-31
A GUI on a server is a liability.  If you want a GUI, install a flavor with a GUI.

What do you mean by > Also, how do I setup server for wifi and 2 windows 11 machines?

---

### Post by rbcc-12 on 2022-11-01
I'm using 22.04.1.  It has no Gui. Is there a ubantu server v?ersion that does?  How it a "liability"?

How do I access my server for playing videos and doing backups from a windows 11 machine?  So they can login to the server to play videos and backup nodes.  
JTM.

---

### Post by guiverc on 2022-11-01
If you want to install the Lubuntu desktop on a Ubuntu Server system, you can use

```

sudo apt install lubuntu-desktop
```

Or if you want a minimal Lubuntu desktop, it's only slightly different

```
sudo apt install --no-install-recommends lubuntu-desktop
```

but either of those will turn your Ubuntu 22.04 LTS Server install, into a Lubuntu 22.04 LTS Desktop system, meaning you'll be using more resources for desktop functions, and have a less efficient server system  (*the server networking will get replaced by NetworkManager used by desktop systems, power settings will change* *reflecting the switch to desktop *etc)

Please note I'm only using Lubuntu as an example; it'll install the full Lubuntu system meaning the LXQt desktop & apps.  Lighter WMs exist, each with it's *pros* & *cons*

---

