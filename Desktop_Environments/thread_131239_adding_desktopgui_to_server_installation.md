---
title: "adding desktop/gui to server installation"
date: 2006-02-16
forum: Desktop Environments
---

### Post by bobtreitman on 2006-02-16
Caveat: I'm a Linux neophyte, so apologies in advance. 
 
I've set up a SAMBA server on 5.10 with excellent instructions from [www.howtoforge.com](www.howtoforge.com) which recommended choosing 'server' at the boot prompt, but realized after the fact that I would like to have a desktop on this system, as well. Can I do this without undoing/redoing all of the server installation (specifically, all the updated packages)? I've got a very slow connection overhere in Tanzania, and really don't want to take up the bandwidth to bring those updates down again.

-bob

---

### Post by dcstar on 2006-02-16
[QUOTE=bobtreitman]Caveat: I'm a Linux neophyte, so apologies in advance. 
 
I've set up a SAMBA server on 5.10 with excellent instructions from [www.howtoforge.com](www.howtoforge.com) which recommended choosing 'server' at the boot prompt, but realized after the fact that I would like to have a desktop on this system, as well. Can I do this without undoing/redoing all of the server installation (specifically, all the updated packages)? I've got a very slow connection overhere in Tanzania, and really don't want to take up the bandwidth to bring those updates down again.

-bob[/QUOTE]
Install the ubuntu-desktop bundle package.

---

### Post by bobtreitman on 2006-02-16
Wow. Thanks for the quick reply.

Dumb question #2. I know how to use 'apt-get install' to do an internet install, but can I install the ubuntu-desktop from the CD to avoid downloading 18+ MBs?

-bob

---

### Post by aysiu on 2006-02-16
[QUOTE=bobtreitman]I've got a very slow connection overhere in Tanzania, and really don't want to take up the bandwidth to bring those updates down again.[/QUOTE] Then don't do this: ```
sudo apt-get update
sudo apt-get install ubuntu-desktop
``` That'll take forever to download and install.

You can do a rather minimalist install with ```
sudo apt-get update
sudo apt-get install x-window-system-core icewm menu synaptic xterm
``` P.S. Kudos to Azz for [this tip](http://www.ubuntuforums.org/showpost.php?p=692882&postcount=8).

---

### Post by aysiu on 2006-02-16
[QUOTE=bobtreitman]Wow. Thanks for the quick reply.

Dumb question #2. I know how to use 'apt-get install' to do an internet install, but can I install the ubuntu-desktop from the CD to avoid downloading 18+ MBs?

-bob[/QUOTE] Yes, actually. Do this: ```
sudo cp /etc/apt/sources.list /etc/apt/sources.list_backup
sudo nano /etc/apt/sources.list
``` Delete **everything** except for this line: ```
deb cdrom:[Ubuntu 5.10 _Breezy Badger_ - Release i386 (20051012)]/ breezy main restricted
``` and make sure there's no # sign in front of the line. Then save (control-x), confirm (y), and exit (Enter). Finally ```
sudo apt-get update
sudo apt-get install ubuntu-desktop
```

---

