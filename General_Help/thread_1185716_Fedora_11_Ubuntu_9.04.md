---
title: "Fedora 11 Ubuntu 9.04"
date: 2009-06-12
forum: General Help
---

### Post by prem1er on 2009-06-12
I have been having some trouble with my Ubuntu 9.04 install lately with some of my hardware (mostly my wired and wireless connections), so I tried out the newest release of Fedora. To my surprise both connections worked much better than they previously worked on Ubuntu 9.04. The wired connection on ubuntu was trying to use the wrong driver (a problem which is well documented on these forums for my card) and the wireless card would always be off when the computer first booted (again well documented).  Also the wireless signal was much weaker on Ubuntu. I have been using Ubuntu for years now, so I am not so familiar with Fedora at all. What are the differences in the distros that would cause my connections to be so much different?  Are the network managers the same in both distros? Thanks in advance.  

Fedora kernel 2.6.29
Wireless - Atheros AR928X Wireless 
Wired - Realtek RTL8111/8168B wired connection

---

### Post by Chemical Imbalance on 2009-06-12
Fedora 11 uses a newer kernel than Jaunty.  That's all I can think off of the top of my head.

You could try using the .29 kernel in Jaunty: [http://kernel.ubuntu.com/~kernel-ppa/mainline/](http://kernel.ubuntu.com/~kernel-ppa/mainline/)

---

### Post by baizon on 2009-06-12
You can try the [Ubuntu 9.10 Alpha 2]("http://www.ubuntu.com/testing/karmic/alpha2"). It got the new kernel as well (2.6.30-rc5).

---

### Post by Chemical Imbalance on 2009-06-12
^^ Alpha isn't a good choice for a stable system.

It's much easier to just install a newer kernel in Jaunty or use Fedora 11.

---

### Post by colau on 2009-06-12
uname -r
```

2.6.29-020629-generic

```

---

### Post by prem1er on 2009-06-12
> **colau said:**
> uname -r
```

2.6.29-020629-generic

```

What does that have to do with my post?

---

### Post by blackxored on 2009-06-12
Well, he actually means the fedora 11 kernel is newer than jaunty's. So there is the most chances that hw-identification is working better for you because of that.

---

### Post by baizon on 2009-06-12
> **Chemical Imbalance said:**
> ^^ Alpha isn't a good choice for a stable system.

It's much easier to just install a newer kernel in Jaunty or use Fedora 11.

Sorry then, i thought didn't know he wants a "stable" Ubuntu/System :-)

---

### Post by colau on 2009-06-12
> **prem1er said:**
> I have been having some trouble with my Ubuntu 9.04 install lately with some of my hardware (mostly my wired and wireless connections), so I tried out the newest release of Fedora. To my surprise both connections worked much better than they previously worked on Ubuntu 9.04. The wired connection on ubuntu was trying to use the wrong driver (a problem which is well documented on these forums for my card) and the wireless card would always be off when the computer first booted (again well documented).  Also the wireless signal was much weaker on Ubuntu. I have been using Ubuntu for years now, so I am not so familiar with Fedora at all. What are the differences in the distros that would cause my connections to be so much different?  Are the network managers the same in both distros? Thanks in advance.  

Fedora kernel 2.6.29
Wireless - Atheros AR928X Wireless 
Wired - Realtek RTL8111/8168B wired connection
You will get something about Fedora 11 NetworkManager [here]("http://fedoraproject.org/wiki/Features/KDE42").
[Wireless]("http://fedoramobile.org/fc-wireless/network-manager/")
[Configuration]("http://fedoramobile.org/fc-wireless/network-manager/")

---

### Post by colau on 2009-06-12
> **prem1er said:**
> What does that have to do with my post?
Fedora kernel is more updated than ubuntu 9.04.

NetworkManager info:
[NetworkManagerFAQ]("http://live.gnome.org/DarrenAlbers/NetworkManagerFAQ/")
[Info1]("http://live.gnome.org/NetworkManagerHardware")
[Info2]("http://projects.gnome.org/NetworkManager/")

---

### Post by Chemical Imbalance on 2009-06-12
> **baizon said:**
> Sorry then, i thought didn't know he wants a "stable" Ubuntu/System :-)

Who doesn't?  :p

---

