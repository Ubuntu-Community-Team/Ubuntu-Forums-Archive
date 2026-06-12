---
title: "can't login to lubuntu netbook"
date: 2012-03-11
forum: Desktop Environments
---

### Post by Azyx on 2012-03-11
I made a lubuntu 11.10 install on a ubuntu 11.04 (eeePC 900) but keep the home-partiton. Lubuntu work very well, but I wish to try lubuntu neetbook, but when I try to login, my password don't seem to work and the login-window just reload. But if I choose 'lubuntu' it work.
/Cheers

---

### Post by SteveDee on 2012-03-12
You are probably missing a few files & folders. Do a search for: netbook

You should find a folder: Lubuntu-Netbook
and files like: startlubuntu-netbook

---

### Post by Azyx on 2012-03-12
> **SteveDee said:**
> You are probably missing a few files & folders. Do a search for: netbook

You should find a folder: Lubuntu-Netbook
and files like: startlubuntu-netbook

1) How can I search for files on the computer in file manager?

2) If i don't have them, where do I find them in synaptic? Have tried to find netbook the, but don't find it för more than Unity and KDE.

PS. I also find gkt2-engine-moblin in repository.

---

### Post by sudodus on 2012-03-12
> **Azyx said:**
> I made a lubuntu 11.10 install on a ubuntu 11.04 (eeePC 900) but keep the home-partiton. Lubuntu work very well, but I wish to try lubuntu neetbook, but when I try to login, my password don't seem to work and the login-window just reload. But if I choose 'lubuntu' it work.
/Cheers
The problem might be that you kept your /home partition. What happens when you run Lubuntu live? (Anyway, I can log into Lubuntu netbook. I prefer the normal Lubuntu desktop environment, but I hope you can test it live, and find out if you need it).

*Edit: It is worth trying the new beta release of Lubuntu Precise. It works very well for me (taking into account that it is beta)*

---

### Post by Azyx on 2012-03-12
> **sudodus said:**
> The problem might be that you kept your /home partition. What happens when you run Lubuntu live? (Anyway, I can log into Lubuntu netbook. I prefer the normal Lubuntu desktop environment, but I hope you can test it live, and find out if you need it).

*Edit: It is worth trying the new beta release of Lubuntu Precise. It works very well for me (taking into account that it is beta)*

What user and password do i need in live-cd?

---

### Post by Azyx on 2012-03-12
> **sudodus said:**
> The problem might be that you kept your /home partition. What happens when you run Lubuntu live? (Anyway, I can log into Lubuntu netbook. I prefer the normal Lubuntu desktop environment, but I hope you can test it live, and find out if you need it).

*Edit: It is worth trying the new beta release of Lubuntu Precise. It works very well for me (taking into account that it is beta)*

I find i could use user 'ubuntu' and empty password to log in to 'Lubuntu', but that don't work on 'Lubuntu Netbook'. So the problems exist even on the Live-CD. Have Lubuntu dropped the support for Lubuntu-Netbook, but still have it in the login (lxdm)?

---

### Post by WasMeHere on 2012-03-12
Hej igen :-)

[s]Maybe you have problems because of some old setting in your /home[/s]. Lubuntu Precise netbook DE worked out of the box for me. It looks like this (after a minimum of tweaking (of the window colours). See the attachment

Olle

*Edit: I just noticed that Lubuntu 11.10 netbook DE does not work live either, so you have more reason to try Lubuntu Precise ;-)*

---

### Post by SteveDee on 2012-03-12
> **Azyx said:**
> 1) How can I search for files on the computer in file manager?...

You can't search in the light-weight file manager PCManFM, but you can install: gnome-search-tool

...however, there is not much point. Just install a clean copy of Lubuntu on an old machine or VirtualBox.

...or, if you want to switch your existing Ubuntu machine to Lubuntu, follow this:-
[http://psychocats.net/ubuntu/purelxde](http://psychocats.net/ubuntu/purelxde)

---

### Post by Azyx on 2012-03-12
> **SteveDee said:**
> You can't search in the light-weight file manager PCManFM, but you can install: gnome-search-tool

...however, there is not much point. Just install a clean copy of Lubuntu on an old machine or VirtualBox.

...or, if you want to switch your existing Ubuntu machine to Lubuntu, follow this:-
[http://psychocats.net/ubuntu/purelxde](http://psychocats.net/ubuntu/purelxde)

1) ok

I have a clean install of Lubuntu, I only saved the home-partition so my files and configurations was left.

Astrange thing isom my 64-bit Ubuntu there I insalled both lulubuntu andxubuntu, to learn and valuate the 3 dist, the Lubuntu Netbook work.

---

### Post by nattomi on 2012-03-16
I had the same problem and I've found this workaround: [http://forum.lxde.org/viewtopic.php?f=8&t=31535](http://forum.lxde.org/viewtopic.php?f=8&t=31535)

---

### Post by Azyx on 2012-03-16
> **nattomi said:**
> I had the same problem and I've found this workaround: [http://forum.lxde.org/viewtopic.php?f=8&t=31535](http://forum.lxde.org/viewtopic.php?f=8&t=31535)

Great, worked fine :) Thanx a lot :)
/Cheers

---

