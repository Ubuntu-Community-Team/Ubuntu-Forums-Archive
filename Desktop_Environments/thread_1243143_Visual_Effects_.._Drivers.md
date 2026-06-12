---
title: "Visual Effects .. Drivers?"
date: 2009-08-18
forum: Desktop Environments
---

### Post by oN dRe on 2009-08-18
Hello :)
I'm new to the Ubuntu OS, just installed it today.
Im a complete Windows user, but I decided to try out Linux, because well, I've heard many places that Linux is a MUST.

Anyways, I downloaded Ubuntu 9.04, and installed it on a Virtual Server.
First thing I did after I installed Ubuntu was mess around with Appearence Preferences.

I went into Visual Effects and tried ticking Extra but I got a popup saying it can't find the necessary drivers.

Where can I find them?
Thanks.

---

### Post by j7%&lt;RmUg on 2009-08-18
Do you have a graphics card apart from the one on your motherboard. If you do what card is it?

If you are running ubuntu on a built in graphics card (like intel or something like that) then you may not be able to run desktop effects.

Hope i can help.

---

### Post by oN dRe on 2009-08-18
Ehh.. Yeah, I'm running on an Intel Graphics Card... :(
Now i have another problem, that maybe you can help with lol.

I went into Synaptic Package Manager, and hit "Reload Package Information." under "Edit".

It Gave me some errors:

Failed to fetch cdrom://Ubuntu 9.04 _Jaunty Jackalope_ - Release i386 (20090420.1)/dists/jaunty/main/binary-i386/Packages  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
Failed to fetch cdrom://Ubuntu 9.04 _Jaunty Jackalope_ - Release i386 (20090420.1)/dists/jaunty/restricted/binary-i386/Packages  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
Some index files failed to download, they have been ignored, or old ones used instead.

---

### Post by j7%&lt;RmUg on 2009-08-18
Hmmm well ill need to do a bit of research on my own jaunty machine but im on a useless windows machine at the moment, until i can get to my PC in 2-3 hours here a question:

Are you running the 32 bit or 64 bit version of ubuntu?

---

### Post by oN dRe on 2009-08-18
Alright sounds good.

Running on 32-bit

---

### Post by andrea000 on 2009-08-18
> **oN dRe said:**
> Ehh.. Yeah, I'm running on an Intel Graphics Card... :(
Now i have another problem, that maybe you can help with lol.

I went into Synaptic Package Manager, and hit "Reload Package Information." under "Edit".

It Gave me some errors:

Failed to fetch cdrom://Ubuntu 9.04 _Jaunty Jackalope_ - Release i386 (20090420.1)/dists/jaunty/main/binary-i386/Packages  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
Failed to fetch cdrom://Ubuntu 9.04 _Jaunty Jackalope_ - Release i386 (20090420.1)/dists/jaunty/restricted/binary-i386/Packages  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
Some index files failed to download, they have been ignored, or old ones used instead.

for your grapic card driver go here

system > administratiion > hardware drivers

on your other problem it seems to be something to
do with not having access to the internet during
install of Ubuntu and it is trying to install something
from the live cd try connecting to the internet and
running sudo apt get update in the terminal other then
that i am unsure of what to do.

---

