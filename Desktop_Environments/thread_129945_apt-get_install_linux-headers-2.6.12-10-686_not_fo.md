---
title: "apt-get install linux-headers-2.6.12-10-686 not found?"
date: 2006-02-15
forum: Desktop Environments
---

### Post by escape on 2006-02-15
Hey, I'm running Breezy and trying to install my ATI drivers but I need linux-headers-2.6.12-10-686; synaptic has linux-headers-2.6.12-9-686, which doesn't cut it. Is linux-headers-2.6.12-10-686 on the ubuntu install CD repository? Is there an easier way to get it besides re-downloading and burning the CD? Thanks...

---

### Post by anirban.sam on 2006-02-15
try,

sudo apt-get install inux-headers-2.6.12-10-686

---

### Post by escape on 2006-02-16
Why would it work on apt-get if it doesn't work on Synaptic? Don't they use the same repositories..?

robert@ubuntu:~$ sudo apt-get update
Get:1 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy Release.gpg [189B]
Get:2 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy-updates Release.gpg [189B]
...
Fetched 2B in 3s (1B/s)
Reading package lists... Done
robert@ubuntu:~$ sudo apt-get install linux-headers-2.6.12-10-686
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package linux-headers-2.6.12-10-686

---

### Post by az on 2006-02-16
[QUOTE=escape]Hey, I'm running Breezy and trying to install my ATI drivers but I need linux-headers-2.6.12-10-686; synaptic has linux-headers-2.6.12-9-686, which doesn't cut it. Is linux-headers-2.6.12-10-686 on the ubuntu install CD repository? Is there an easier way to get it besides re-downloading and burning the CD? Thanks...[/QUOTE]

linux-image-2.6.12-9-386 is on the install cd along with linux-headers-2.6.12-9-386.  Any other versions of the kernel are only found on the online repositories.  You need to get access to the net, enable the main repositories and update and you will be able to install both the latest kernel for 686 (install linux-686) and the headers for it (linux-headers-686)

How did you install the linux-image-686 kernel?

---

### Post by escape on 2006-02-18
[QUOTE=azz]linux-image-2.6.12-9-386 is on the install cd along with linux-headers-2.6.12-9-386.  Any other versions of the kernel are only found on the online repositories.  You need to get access to the net, enable the main repositories and update and you will be able to install both the latest kernel for 686 (install linux-686) and the headers for it (linux-headers-686)

How did you install the linux-image-686 kernel?[/QUOTE]

I got the 686 kernel from a howto here, I think it was just through synaptic. I might check that thread again. I just redownloaded the CD, but if it has the headers for 2.6.12-9, I guess that won't work. I think I didn't have the right repositories enabled though, since I just got synaptic to find the right headers. Thanks guys!

---

### Post by Syphin on 2006-02-18
I sounds like you dont have the repo needed for it, enabled.

Either way, you could get it from packages.ubuntu.com if all else fails.
[http://packages.ubuntu.com/breezy/devel/linux-headers-2.6.12-10-686](http://packages.ubuntu.com/breezy/devel/linux-headers-2.6.12-10-686)

heres my sources if interested to see if your missing anything.
/etc/apt/sources.list  (note, I dont have the src repos in there cause i got a slow connection. :P )
```
deb http://archive.ubuntu.com/ubuntu breezy main restricted
## Bug fixes
deb http://archive.ubuntu.com/ubuntu breezy-updates main restricted
## Universe'
deb http://archive.ubuntu.com/ubuntu breezy universe multiverse
## Security
deb http://security.ubuntu.com/ubuntu breezy-security main restricted
deb http://security.ubuntu.com/ubuntu breezy-security universe multiverse
## Backports
deb http://archive.ubuntu.com/ubuntu breezy-backports main restricted universe multiverse
## plf primary
deb http://packages.freecontrib.org/ubuntu/plf/ breezy free non-free
## plf secondary
# deb ftp://ftp.free.fr/pub/Distributions_Linux/plf/ubuntu/plf/ breezy free non-free
## plf mirror
# deb http://public.planetmirror.com/pub/plf/ubuntu/plf/ breezy free non-free
## wine
# deb http://wine.sourceforge.net/apt/ binary/
## Gdebi
deb http://people.ubuntu.com/~mvo/gdebi /
## Oo2 final
deb http://people.ubuntu.com/~doko/OOo2 ./
```

//Edit:
bah didnt read your last post. :p  ignore me.. lol   Glad ya got it worked out :)

---

