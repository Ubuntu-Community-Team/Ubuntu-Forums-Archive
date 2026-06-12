---
title: "how do I tell if I have 32 or 64 bit?"
date: 2009-01-31
forum: General Help
---

### Post by badperson on 2009-01-31
My version of vista (I'm dual booting...) is 32, also, I have different os's on different drive, so I'm going to wipe everything and start over...

I'd like both ubuntu and vista to be 64 bit...is it a different iso image for ubntu to have 64 bit? 

Also, I don't see it indicated anywhere in the system monitor...how can I find out what version I have? 
bp

---

### Post by albinootje on 2009-01-31
> **badperson said:**
> I don't see it indicated anywhere in the system monitor...how can I find out what version I have? 
Try the following in a terminal :
```

uname -m

```

There's a different iso indeed, e.g. : [http://releases.ubuntu.com/8.04.2/](http://releases.ubuntu.com/8.04.2/)
-> here's a 64 bit Ubuntu installation cdrom : [http://releases.ubuntu.com/8.04.2/ubuntu-8.04.2-desktop-amd64.iso](http://releases.ubuntu.com/8.04.2/ubuntu-8.04.2-desktop-amd64.iso)

---

### Post by taurus on 2009-01-31
If you want to find out which version of kernel you are running, open a terminal and run this little command.

```
uname -m
```
If it says i686, then you are using x86 (32bit) but if it says x86_64, then you are running the 64bit kernel.

---

### Post by badperson on 2009-01-31
thanks so much, I have this...

```
i686
```

and searching around has shed light on another little issue I've been having with my soundcard...

> Good news for owners of Creative Sound Blaster X-Fi series as manufacturer’s binary Linux drivers are available for free downloading. The driver is compatible with ALSA. Bad news: it’s available only for x86_64 Linux.

thanks a lot, with my next install I'll make sure to get the 64 bit iso.
bp

---

