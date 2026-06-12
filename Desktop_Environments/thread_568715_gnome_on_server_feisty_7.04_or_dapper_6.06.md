---
title: "gnome on server: feisty 7.04 or dapper 6.06"
date: 2007-10-06
forum: Desktop Environments
---

### Post by elfenau on 2007-10-06
when i issue the cli command sudo apt-get install ubuntu-desktop it fails to execute with error 'Couldnt find package ubuntu-desktop' I assume this is because it cant see the cd where the install in located. i have forgotten how to issue the mount command to make the cd accessible to the cli (last used unix many years ago). Or is there another way. All i want is Gnome on the server so i can more easily learn how to administer the networking and  lamp properties of server (versions 6.06 or 7.04). Can anyone enlighten me :)

---

### Post by pheeror on 2007-10-06
First of all, you need to read basic documenation/handbooks. It's really better to read something about topic, then solving it in try-try-try-'**** it still doesn't work' manner.
I don't think there are some click'n'almostwork tools in gnome for LAMP installation. If you want setup shared hosting, check out syscp,vhcs or cpanel,plesk. 

```

mount /media/cdrom0

```
This is ubuntu line, I don't think there is unix system using /media :-D

Anyway, I would prefer setting up internet sources (edit /etc/apt/sources.list) to dealing with obsolote media like cdrom. 

And of course you have to run 
```

apt-get update

```
to sync package list.

---

### Post by elfenau on 2007-10-06
thanks for that - i have just been out and bought a book :) - my question really was a response to other posts on the problem which implied that the gnome install  was just a case of using the apt-get command - which it aint.

---

