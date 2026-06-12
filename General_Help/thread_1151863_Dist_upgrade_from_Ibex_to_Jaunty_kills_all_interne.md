---
title: "Dist upgrade from Ibex to Jaunty kills all internet access"
date: 2009-05-07
forum: General Help
---

### Post by sleepitoff on 2009-05-07
After a dist upgrade from Ibex to Jaunty, I have no ability to use the internet at all. Wired or wireless. I have the icon in the system tray and network manager is there, it just doesn't work and I can't and don't know how to make it connect

I had to create a seperate partition and install 8.10 again just so I could get back on-line. 

What do I have to do? I did see some threads like this, but no answer. 

Right now I'm thinking reinstall Network Manager, but how do I do that? I'm guessing that I could download all the files on this partition and manually add them to my jaunty partition. 

If anyone could please help, that would be great. I really need to get the internet working again on that partition.

---

### Post by decoherence on 2009-05-07
Hi,

We need some information about your hardware and configuration. Please post the output of the following terminal commands (get to the terminal from Applications > Accessories > Terminal)

```
ifconfig
```

```
sudo lshw -C network
```

---

### Post by prem1er on 2009-05-07
Also, this would help.

```
lspci
```

---

