---
title: "[xubuntu] Using next LTS daily build for new PC?"
date: 2018-03-19
forum: Desktop Environments
---

### Post by adfgqi on 2018-03-19
Hi, I'm going to be building a new PC later this week. I like using the LTS-es because I don't like the hassle of upgrading all the time. Given how close the next LTS is, how painless (or painful) would it be to use a daily build of the next LTS and upgrade that later next month, compared to doing a full re-install? I've tried dist-upgrade in the past and it wasn't exactly a smooth experience (although that was quite some years ago).

---

### Post by monkeybrain20122 on 2018-03-19
If you want to do bug testings and enjoy the occasional crashes, go ahead.

---

### Post by adfgqi on 2018-03-19
Well, I realize that it not going to be 100% stable, and that's ok (up to a point). I generally wait for the .1. What would you propose I do instead? dist-upgrade from 17.10 or 16.04 when that time comes? Or just do a fresh install from 16.04 three months or so from now (leaning towards this option).

---

### Post by kerry_s on 2018-03-19
go for it, do it, do it, do iiittt!

lol, the crashes have been mostly, the auto update & mail for me, but they recover.
just clean out the crash folder & you won't be bugged. 
sudo rm /var/crash/*

not a big deal.

if you do the minimal install, there'll be less apps to go buggy. then you can cherry pick what you want to use.

---

### Post by adfgqi on 2018-03-19
Yeah I run most things I need to trust to be stable in Docker containers and VMs. Here's (off the top of my head) what I need to be stable on the host:

- The kernel (obviously)
- Docker
- Virtualbox 
- XFCE (fairly minimal usage)
- Triple monitor support
- OpenJDK
- Chromium and Firefox

---

### Post by kerry_s on 2018-03-19
well, there you go then. your only choice is 16.04 lts

all that stuff worked fine last i used 16.04

---

### Post by adfgqi on 2018-03-19
:P

Gonna have to upgrade at some point though.

---

### Post by kerry_s on 2018-03-19
that's a given.

right now both 17 & 18 are iffy if you need your stuff to work. xubuntu 17 had a crashy installer so i didn't bother with that. like i said xubuntu 16 was fine.
i just installed pop!_os a few hours ago, it's based on ubuntu 17.10 made by system 76, seems to run just fine, it's a gnome ui.
before that i had solus, but didn't dig bugie de & there gnome & mate editions just felt half ass.

you can always try it for yourself anyway, some just have better luck with there hardware.

---

### Post by adfgqi on 2018-03-19
Ok. I guess I will stick with 16.04 for at least another 6 months then.

---

