---
title: "Help installing Synergy"
date: 2009-02-18
forum: General Help
---

### Post by jimloomis on 2009-02-18
Hey guys,

I was just wondering how to install Synergy on Ubuntu and Xubuntu. When I try to do it with the terminal, I get this:

jimmy@jimmy-compaq:~$ apt-get install synergy
E: Could not open lock file /var/lib/dpkg/lock - open (13 Permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?
jimmy@jimmy-compaq:~$ 

This happens on all of my Linux machines. How do I get around this?
 I would install it by compiling the source, but I'm a total newb and really don't know how to even get started with that. Any ideas?

Can anyone just write an install command for the source?

Thanks,
Jim

---

### Post by Shazaam on 2009-02-18
You need to be root (sudo)...
```
sudo apt-get install synergy
```

---

### Post by jimloomis on 2009-02-18
So I would type "sudo apt-get install synergy"?

I'll try it... thanks!

---

### Post by jimloomis on 2009-02-19
It worked! I tried using the six-step tutorial to get it running, but can't find synergy.conf after creating it via the terminal. Any ideas?

---

### Post by mbeach on 2009-02-19
not sure which tutorial you used, but I believe you can put the synergy.conf in your home folder if you like.

[https://help.ubuntu.com/community/SynergyHowto](https://help.ubuntu.com/community/SynergyHowto)

edit:
or type 
```
locate synergy.conf
```
to see where it is.

---

