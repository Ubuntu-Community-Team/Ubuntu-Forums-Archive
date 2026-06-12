---
title: "Is mplayer in apt-get ?"
date: 2005-12-28
forum: General Help
---

### Post by d11wtq on 2005-12-28
I'm having a really hard time using apt-get.... it looks as if there's hardly anything available :( 

Is mplayer even in there?

Another question.... if i were to get some .deb files myself can I use apt-get to install them so it doesn't have dependency confilcts?

Thanks :)

---

### Post by spincricket on 2005-12-28
you can get mplayer through apt-get 
```
sudo apt-get install mplayer-386
sudo apt-get install mplayer-fonts
```
I'd make sure you have the right repositories enabled. ie, multiverse/universe. then ```
sudo apt-get update
```. This should solve any issues with other packages also. Apt-get is awesome, second to PORTAGE.

---

### Post by d11wtq on 2005-12-28
[QUOTE=spincricket]you can get mplayer through apt-get 
```
sudo apt-get install mplayer
```
I'd make sure you have the right repositories enabled. ie, multiverse/universe. then ```
sudo apt-get update
```. This should solve any issues with other packages also. Apt-get is awesome, second to PORTAGE.[/QUOTE]

I tried (as root using `su') `apt-get install mplayer' but it said mplayer isn't found :(

How do I ensure I have the right repositories?  This is a fresh install (last night) so should they already be OK?

I've been told apt-get is great but I'm having these problems finding packages (even searching with apt-cache).  Portage rocks yeah... I'm a Gentoo user trying out Ubuntu to see if it fits my desktop requirements better (i.e. not waiting 48 hrs for GNOME to compile :P).

Thanks for pointing me in the right direction :D

EDIT | ```

root@w3style:~# sudo apt-get -s install mplayer
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package mplayer

```

---

### Post by d11wtq on 2005-12-28
Duh! /etc/apt/sources.list :)

Fixed thanks -- wow it's a wonder I could install anything at all :P

---

