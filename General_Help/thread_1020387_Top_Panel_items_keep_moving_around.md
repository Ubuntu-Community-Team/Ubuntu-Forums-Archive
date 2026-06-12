---
title: "Top Panel items keep moving around"
date: 2008-12-24
forum: General Help
---

### Post by Heeter on 2008-12-24
Hi all,

Upon bootup, the few panel items I have across the top always move around, lots of times it ends up in the middle of the panel.

How can I fix this?

Thanks

Heeter

---

### Post by plucky on 2008-12-24
Right click on the icons and make sure **Lock to panel** is ticked.
Also if there are too many items on the panel can cause them to move.Leave space for program icons to open.

Good Luck

---

### Post by kaibob on 2008-12-24
I don't know if this will help, but the configuration editor has an option to globally lock down the panels. It only takes a few seconds to give it a try. The key is:

/apps/panel/global/locked_down

---

### Post by Heeter on 2008-12-25
they are still all over the panel on reboot.

Is there anything else I can try?


Heeter

---

### Post by KrazyPenguin on 2009-01-01
same prob here!!!

---

### Post by Heeter on 2009-01-01
right now they are somewhere in the middle of the screen, and not letting anything on the right of it. I have all these opened on the left, all crushed up.

locked in or not, they aren't going to move from the middle.


Heeter

---

### Post by linuxisevolution on 2009-01-01
This is a gnome problem... You could try a better desktop enviorement. Open synaptic  via system >> admin >> synaptic and search for lxde . tick the check box of it and click ok or accept whatever pops up. Then click apply. After the install finnishes, log out and select "sessions" and "lxde from the menu before logging in. You will be greeted with a faster and ( in my opinion ) nicer-looking desktop. I had the same problem on Gnome with a 550mhz 128mb system with 16mb video. It was the video drivers that caused the stuff to move around... I still suggest not using Gnome, there isn't a good use for it :)

---

### Post by KrazyPenguin on 2009-01-02
So is this a bug, it happened in other gnome versions as well.
For a while my laptop was working fine, and then recently the icons on th e panel are moving all over the place.
It doesn't matter if they are locked or not. 
The computer boots and they are moved.
Thanks

---

### Post by KrazyPenguin on 2009-01-02
Ok I did a google and found the answer in case anybody was wondering.

[https://bugs.launchpad.net/gnome-panel/+bug/44082](https://bugs.launchpad.net/gnome-panel/+bug/44082)

Basically it is still a bug in 8.10.

It hasn't been fixed yet, it is very annoying and I will be switching desktop environments until fixed.

I'm not sure which one yet.

Thanks.

---

### Post by Heeter on 2009-01-02
Awesome,

Thanks for your research,

Now I know I am not the only one.

Heeter

---

### Post by oldsoundguy on 2009-01-02
a work around:

I found that IF I place the item (drag it to the desired location) and lock it (an option by right clicking) it seems to stay put.. also going into the menu and adding a separator bar between items has made it rock solid on 5 various machines .. (3 - 8.10, 1 - Linux Mint, 1 - Mythbuntu.)

---

