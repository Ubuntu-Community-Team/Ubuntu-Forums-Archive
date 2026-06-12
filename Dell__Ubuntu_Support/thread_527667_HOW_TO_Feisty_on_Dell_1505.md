---
title: "HOW TO: Feisty on Dell 1505"
date: 2007-08-16
forum: Dell  Ubuntu Support
---

### Post by Matthew Wiebelhaus on 2007-08-16
[CENTER][COLOR="Red"][SIZE="7"]HOW TO: FEISTY ON DELL E1505[/SIZE][/COLOR]

First i would like to say these are the :)specifications:mad: of my guide 
[LIST=1]
[*]Dell E1505
[*]Intel 945 Graphics Card
[*]Intel 3945 Wireless card
[/LIST]

[CENTER]This is a short and simple guide for a dell E1505 to enable all your hardware[/CENTER]


[SIZE="3"]First boot from the the Ubuntu feisty live cd
Second Install Feisty (I suggest using the whole disk
Third After installing feisty boot from your hard drive and log in
Fourth Install Updates
Fifth open up the synaptic package manager (System -> Administration -> Synaptic Package Manager) and install  **xserver-xorg-video-intel** this will enable higher resolution
You are done support will be added for better graphic cards later[/SIZE]   [/CENTER]

---

### Post by tgm4883 on 2007-08-16
> **Matthew Wiebelhaus said:**
> [CENTER][COLOR="Red"][SIZE="7"]HOW TO: FEISTY ON DELL E1505[/SIZE][/COLOR]

First i would like to say these are the :)specifications:mad: of my guide 
[LIST=1]
[*]Dell E1505
[*]Intel 945 Graphics Card
[*]Intel 3945 Wireless card
[/LIST]

[CENTER]This is a short and simple guide for a dell E1505 to enable all your hardware[/CENTER]


[SIZE="3"]First boot from the the Ubuntu feisty live cd
Second Install Feisty (I suggest using the whole disk
Third After installing feisty boot from your hard drive and log in
Fourth Install Updates
Fifth open up the synaptic package manager (System -> Administration -> Synaptic Package Manager) and install  **xserver-xorg-video-intel** this will enable higher resolution
You are done support will be added for better graphic cards later[/SIZE]   [/CENTER]

How does the xserver-xorg-video-package differ from installing the 915resolution package?  I installed the 915resolution package on my E1505 and enabled the widescreen that way.

---

### Post by Matthew Wiebelhaus on 2007-08-16
915resolution is a BIOS hack 
the intel driver is the intel drive the intel x-xorg-server

---

### Post by tgm4883 on 2007-08-16
Sweet, i'll change it up then

---

### Post by Matthew Wiebelhaus on 2007-08-16
Also i think the x-xorg is made by intel and 915resolutions is made by some linux smarty =)

---

