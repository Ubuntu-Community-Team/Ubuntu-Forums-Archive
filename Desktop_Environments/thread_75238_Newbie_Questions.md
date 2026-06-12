---
title: "Newbie Questions"
date: 2005-10-13
forum: Desktop Environments
---

### Post by tkonicz on 2005-10-13
Ok, this are my first hours with thist distribution, and I have some rather easy questions for the advances users.
1. Where do I get the software for mp3-playback? (gstreamer-lib?)
2. Where do I get w32 codecs?
3. I have used Mandrake, and there where so-called "contrib" software on the net, which was not officially included and  it could be used by everyone. Is there something simmilar in ubuntu, are there any software, which can be inclubed via synaptic to my softwarelist?

thanks in advance,
Tomasz

---

### Post by troywill1 on 2005-10-13
Check this out:

[https://wiki.ubuntu.com/RestrictedFormats](https://wiki.ubuntu.com/RestrictedFormats)

Troy

---

### Post by joelito on 2005-10-13
add the following lines to your sources.list
```

deb http://ftp.debian.org/debian/ sarge main
deb http://ftp.nerim.net/debian-marillat/ sarge main

```
and these to your /etc/apt/preferences (create it if it doesn't exist)
```

Package: *
Pin: release o=Ubuntu
Pin-Priority: 900

Package: *
Pin: release o=Debian
Pin-Priority: 800

```

Then:
```

sudo apt-get update
sudo apt-get install mplayer w32codecs libdvdcss2

```
This could help you mix Debian Stable(sarge) and Ubuntu Stable(Breezy) and get the obscured copyright(DMCA) limited packages. Consider it civil disobedience

---

### Post by tkonicz on 2005-10-13
thank you.

---

### Post by H_Roark on 2005-10-13
[QUOTE=joelito]add the following lines to your sources.list
```

deb http://ftp.debian.org/debian/ sarge main
deb http://ftp.nerim.net/debian-marillat/ sarge main

```
and these to your /etc/apt/preferences (create it if it doesn't exist)
```

Package: *
Pin: release o=Ubuntu
Pin-Priority: 900

Package: *
Pin: release o=Debian
Pin-Priority: 800

```

Then:
```

sudo apt-get update
sudo apt-get install mplayer w32codecs libdvdcss2

```
This could help you mix Debian Stable(sarge) and Ubuntu Stable(Breezy) and get the obscured copyright(DMCA) limited packages. Consider it civil disobedience[/QUOTE]


No go.  I get text advising me that w32codecs is a virtual package, that I should chose one program from a list to install, and that no installation candidate is found.  When I try to install those packages, it claims it can't find them--the packages it just listed, it can't frigging find. 
Anyway, is there another way to do this?
Download from the mplayer site doesn't work.
Easy Ubuntu doesn't work

---

### Post by vrecan on 2005-10-13
The easiest way to get mp3 playback is to just uncomment universe source in your /etc/apt/sources.list

then just open up synaptic by going to system->administration->synaptic

and do a search for gstreamer and install all the plugins.. there is a package that depends on all the gstreamer plugins but I can't recall the exact name of it.

---

### Post by H_Roark on 2005-10-13
I got it working by using the totem-xine instructions found in the unofficial guide under codecs.

---

