---
title: "Removing Xfce from Kubuntu 7.10"
date: 2007-10-30
forum: Desktop Environments
---

### Post by dorkdork777 on 2007-10-30
I've installed xubuntu-desktop from my Kubuntu 7.10 installation with aptitude from the Terminal, but I'd like to remove it. I did 'sudo aptitude remove xubuntu-desktop', it went through successfully, but I was still able to log into Xfce, and all the Xubuntu applications (AbiWord, Xfce 4 Appfinder, Synaptic, etc) are still there.

How would I go about getting rid of all of these apps  that were installed when I installed xubuntu-desktop?

Thanks in advance for the replies!

---

### Post by rsambuca on 2007-10-30
[http://www.psychocats.net/ubuntu/purekde](http://www.psychocats.net/ubuntu/purekde)

---

### Post by dorkdork777 on 2007-10-30
Thanks, I tried that, but I got this - 

> 
Reading package lists... Done
Building dependency tree
Reading state information... Done
Package gstreamer0.10-gnomevfs is not installed, so not removed
Package libgsf-gnome-1-114 is not installed, so not removed
E: Couldn't find package xubuntu-artwork-us


Any more help? I read that you can search for xfce4 in Syanptic, and mark them for complete removal - can the same thing be done in Adept? If so, would I request removal or purging?

---

### Post by bingoUV on 2007-10-30
I have never tried this, as I am a hands-on guy (if it is a few packages, I would remove them by name). But you have too many packages to auto remove, so you can try
```

sudo apt-get autoremove

```

The apt-get man page says it should do what you want to : 
```

       autoremove
           autoremove is used to remove packages that were automatically installed to satisfy
           dependencies for some package and that are no more needed.

```

---

