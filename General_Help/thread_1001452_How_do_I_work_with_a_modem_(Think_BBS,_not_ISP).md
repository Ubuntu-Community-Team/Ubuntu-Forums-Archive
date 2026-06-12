---
title: "How do I work with a modem? (Think BBS, not ISP)"
date: 2008-12-03
forum: General Help
---

### Post by gumpish on 2008-12-03
So I have a laptop (Latitude D800) that has an on-board modem that I need to use to dial into my building's PBX as if I were dialing a BBS, not an ISP (it's ok, I'm legit).

Previously we'd used some terminal software under Windows, but that old laptop is gone and I thought surely there must be something equivalent for Linux...

Running up to date Hardy on the laptop. What package lets me talk to my modem? (I searched packages.ubuntu.com and couldn't seem to get meaningful results.)

Help appreciated.

(edit: typos)

---

### Post by gumpish on 2008-12-05
Just to answer my own question (in case this post turns up in someone's google search):

The scanModem program is very helpful. Tells you what you have, what you need to make it work and where to get it.

[http://linmodems.technion.ac.il/]("http://linmodems.technion.ac.il/")

With Hardy you have to install some ALSA-related package, which builds a kernel module which takes a pretty long time...

But yeah, once I installed everything suggested by the scanModem utility I was able to use the minicom package to issue AT commands to my modem and dial out as needed.

---

