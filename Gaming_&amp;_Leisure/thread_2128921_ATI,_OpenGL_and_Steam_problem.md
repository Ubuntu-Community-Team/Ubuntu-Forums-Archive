---
title: "ATI, OpenGL and Steam problem"
date: 2013-03-24
forum: Gaming &amp; Leisure
---

### Post by Hyper Tails on 2013-03-24
Hey guys, I have Ubuntu 12.10 with an ATI Radeon HD 5770.

I've installed Steam so I could play Team Fortress 2. However, After installing Steam, and trying to launch Team Fortress 2, I get this message: [ATTACH=CONFIG]240510[/ATTACH]

Any help will be thanked.

---

### Post by Perfect Storm on 2013-03-24
Make sure to install the latest restricted driver: [https://wiki.ubuntu.com/Valve#AMD.2BAC8-ATI_Graphics](https://wiki.ubuntu.com/Valve#AMD.2BAC8-ATI_Graphics)

---

### Post by ManamiVixen on 2013-03-24
AI, I don't think Steam has the best advice. It suggests enabling the Pre-Release Repo in Ubuntu. That could be trouble.

---

### Post by Perfect Storm on 2013-03-24
If the default restricted driver doesn't work, he could give it try.

---

### Post by Hyper Tails on 2013-03-24
When I use the restricted drivers, I get no unity when I log back in.

---

### Post by ManamiVixen on 2013-03-24
The only other option is xorg-edgers if you are up to it.

---

### Post by Hyper Tails on 2013-03-24
Would I need to use Synaptic Package Manager to do that?

---

### Post by ManamiVixen on 2013-03-24
Here, be aware you could get the same error as before or worse. This is bleeding edge software:

sudo add-apt-repository ppa:xorg-edgers/ppa
sudo apt-get update
sudo apt-get remove --purge nvidia-current **AND/****OR** sudo apt-get remove --purge nvidia-current-updates
sudo apt-get install nvidia-313

There. :)

Edit: I'm an idiot. Thats for Nvidia, not ATI. Unfortunately I have no experience installing an ATI driver. BUT Xorg-Edgers will help. I swear, it has the ATI driver in it.

---

### Post by ManamiVixen on 2013-03-24
Yeah just ignore me. I'm going to curl in a corner now.

---

### Post by Perfect Storm on 2013-03-25
According to this guy on steam, it requires it a bit of tweaking to get Team Fortress 2 to work with an ATI HD card: [http://steamcommunity.com/app/221410/discussions/4/846939615100594781/?l=english#p1](http://steamcommunity.com/app/221410/discussions/4/846939615100594781/?l=english#p1)

and [http://steamcommunity.com/app/221410/discussions/1/882966056717055843/#p2](http://steamcommunity.com/app/221410/discussions/1/882966056717055843/#p2) with the same card as you. 

To sum it up; Seems to be a hit or miss regarding Team Fortress 2 if you're using ATI card.


*EDIT:* ManamiVixen I also got Nvidia card ;)

---

