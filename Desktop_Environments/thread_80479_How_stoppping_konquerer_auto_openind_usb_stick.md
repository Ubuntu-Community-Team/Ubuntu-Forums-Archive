---
title: "How stoppping konquerer auto openind usb stick?"
date: 2005-10-22
forum: Desktop Environments
---

### Post by Matchless on 2005-10-22
Hi,
    How can I stop konquerer atomatically opening my usb memery stick when I plug it in?

---

### Post by mlomker on 2005-10-22
That's actually a program called **ivman** that is new with Breezy.  You could open Kynaptic and remove it if you want to disable autoplay.  Modifying the behavior is more complicated because ivman uses XML configuration files that aren't that nice to look at.

---

### Post by GeneralZod on 2005-10-22
[QUOTE=mlomker]That's actually a program called **ivman** that is new with Breezy.  You could open Kynaptic and remove it if you want to disable autoplay.  Modifying the behavior is more complicated because ivman uses XML configuration files that aren't that nice to look at.[/QUOTE]

Thanks for this little snippet of info - I've had a bug since installing Kubuntu where whenever media is inserted, *two* konqueror windows pop-up.  You tip pointed me to a solution (I had two instances of ivman running, for some reason!).

Hopefully I'll be able to find where they are spawned and ensure only one starts up at boot...

---

### Post by mlomker on 2005-10-22
> Hopefully I'll be able to find where they are spawned and ensure only one starts up at boot...

Here's an [earlier thread]("http://www.ubuntuforums.org/showthread.php?t=70092") about it.

---

### Post by Matchless on 2005-10-22
[QUOTE=mlomker]That's actually a program called **ivman** that is new with Breezy.  You could open Kynaptic and remove it if you want to disable autoplay.  Modifying the behavior is more complicated because ivman uses XML configuration files that aren't that nice to look at.[/QUOTE]

mlomker,
              Thanks for the info. I rather uninstalled Ivman and also had to reboot before it cleared. If need be I can always reinstall from the install disk.
This looks like a great program, but definitely needs a nice gui to allow easy configuring by the user. 
Your speedy response is appreciated.

---

### Post by mlomker on 2005-10-22
> This looks like a great program, but definitely needs a nice gui to allow easy configuring by the user. 


That probably won't happen because autoplay is built into KDE 3.5 and Drake will have that by default.  Ivman was just a temporary solution for autoplay with KDE 3.4.x.

---

### Post by Parkotron on 2005-10-29
Excellent news. I'm currently ripping several CDs and this was driving me nuts. Also good to hear that autoplay will be integrated into KDE 3.5.

---

### Post by greatshape on 2005-10-29
[QUOTE=mlomker]That probably won't happen because autoplay is built into KDE 3.5 and Drake will have that by default.  Ivman was just a temporary solution for autoplay with KDE 3.4.x.[/QUOTE]

I have a little problem with this too since i upgraded to breezy.
When i load a blanc cd-r into my writer, konqueror opens and gives me this message: (translated myself from my native language)
```

There was a fault loading media:/hdc:
The file or directory media:/hdc doesn't exist.

```
When i try to mount the (blanc) cd-r i get:
```

mount: wrong fs type, bad option, bad superblock on /dev/hdc,
missing codepage or other error
In some cases useful info is found in syslog - try
dmesg | tail or so

```
Though everything works fine, i can write cd's :-) 

regards, steve

---

