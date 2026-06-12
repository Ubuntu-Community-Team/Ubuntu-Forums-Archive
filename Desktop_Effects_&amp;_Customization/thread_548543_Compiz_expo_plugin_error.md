---
title: "Compiz expo plugin error?"
date: 2007-09-11
forum: Desktop Effects &amp; Customization
---

### Post by GatorV on 2007-09-11
Whenever I load up the Expo Plugin, there seems to be some kind of error because compiz stops working and I have to reload it?

What can the error be?

Thanks in advance.

---

### Post by Vadi on 2007-09-11
Start compiz in the terminal, then when compiz dies it'll write a whole bunch of stuff to it, which will help figure out what's wrong.

So go to applications - accessories - terminal and type "compiz --replace". When it dies, copy/paste the output here :)

---

### Post by richardgundersen on 2007-09-17
Hi

I have exactly the same problem. I've started compiz in a terminal and this is what happens when Expo crashes. Would really appreciate any help because Expo is, in my opinion, one of the best plugins in Compiz. I would love to be able to use it

***********************************
Segmentation fault (core dumped)
Window manager warning: "" found in configuration database is not a valid value for keybinding "toggle_shaded"
***********************************

---

### Post by richardgundersen on 2007-09-17
BTW I turned off almost all plugins. The only ones I have installed are

Window decoration
All Image loading plugins
Dbus
Regex matching

I saw another post suggesting turning off the screensaver plugin, but I don't even seem to have that one available. 

Synaptic says I'm using Compiz 0.5.2
My graphics card is an NVIDIA 8800 GTS using driver version 100.14.11

Thanks! :)

---

### Post by Vadi on 2007-09-17
Edit: Nevermind. I have no idea then. Who's repository are you using?

---

### Post by richardgundersen on 2007-09-17
Hi

I'm using this repository

      deb [http://ppa.launchpad.net/amaranth/ubuntu](http://ppa.launchpad.net/amaranth/ubuntu) feisty main

which was referenced in this tutorial

   [http://forlong.blogage.de/article/2007/8/26/The-best-way-to-install-Compiz-Fusion-on-Ubuntu-Feisty](http://forlong.blogage.de/article/2007/8/26/The-best-way-to-install-Compiz-Fusion-on-Ubuntu-Feisty)

Any help would be great. If there are some other logs I could post pls let me know and I will be happy to. Really want to use the Expo plugin!

BTW I also have to reinstall my NVIDIA driver every time I reboot (!) Not sure if this is related but thought I would mention it. :)

---

### Post by Vadi on 2007-09-17
That's a good guide. Unfornutately I don't know much about nvidia cards, have an ati one myself. 

There's a page about nvidia cards here ([click]("http://compiz.org/NVidia")), see if that helps you not reinstall.

---

### Post by richardgundersen on 2007-09-17
Hey, thanks. It looks like the link you sent will be useful. I hadn't disabled nv so trying that first. Will have a play and post back my findings

Thanks again

---

### Post by Forlong on 2007-09-17
Could you please elaborate on what you do, when expo crashes?
There's a bug, when you double-click in expo mode on a desktop. You don't have to do that, just use your right mousebutton for that.

---

### Post by richardgundersen on 2007-09-18
Aha, thanks Forlong. I am indeed double-clicking on the desktop in Expo mode, which is when it crashes. I'll try right-clicking instead when I get home. 

If it's a bug then that's great (sort of) - at least I know my drivers are all set up correctly which is what I was worried about. 

Thanks for clearing that up for me - appreciate it.

---

