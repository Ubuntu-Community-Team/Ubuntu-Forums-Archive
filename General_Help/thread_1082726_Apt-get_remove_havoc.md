---
title: "Apt-get remove havoc"
date: 2009-02-28
forum: General Help
---

### Post by chemicalfan on 2009-02-28
I'm an idiot. I just crippled my system by running 'sudo apt-get remove python', and ignoring the warnings about it removing hundreds of packages. I did this to try and get Python 2.5.2 off and get 2.6.1 on it (I later figured that I'll have to keep 2.5.2, for all of those packages that needed it)

Basically, I can boot into X fine, but I can't get internet access working to download the packages again. Normally I use wireless, but Wicd is gone, so I thought I'd try the wired connection, but I don't have a network manager at all. Is it possible to configure the connection in the terminal? If so, please could someone provide a script for me? I'm on a DHCP router, so it should be a piece of cake (except I'm a total noob - although not one afraid of breaking things, apparently!)

---

### Post by heindsight on 2009-02-28
Try doing:

```
echo -e "auto eth0\niface eth0 inet dhcp" | sudo tee -a /etc/network/interfaces
sudo invoke-rc.d networking restart
```

---

### Post by chemicalfan on 2009-02-28
Oh, you legend!!!! It's times like these that I wish this forum had a rep button (well, still did)

How did you know that? I need to learn this kind of stuff

---

### Post by heindsight on 2009-02-28
> **chemicalfan said:**
> 
How did you know that? I need to learn this kind of stuff
I don't know, years of experience maybe? ;)

---

