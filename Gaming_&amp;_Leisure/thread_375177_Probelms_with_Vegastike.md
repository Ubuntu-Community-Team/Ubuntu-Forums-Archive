---
title: "Probelms with Vegastike"
date: 2007-03-03
forum: Gaming &amp; Leisure
---

### Post by Darth Trix on 2007-03-03
I apt-get vegastrike 0.4.3 but vslaunch is nowhere.
I can play the game executing vegastrike but that just drops me in the middle of the game.
I can't also configure the game vsinstall does the same as vegastrike and when i excecute vssetup i get this:

> can't read setup.conf

What is happening?

---

### Post by kthakore on 2007-03-03
the apt-get method is broken for some reason get vegastrike form the website in .deb mode. Also I must warn you I have only ever gotten vegastrike to work properly on fedora and gentoo. It just refuses to work on ubuntu. Or might just be me.

---

### Post by Sinthramyr on 2007-10-01
> **Darth Trix said:**
> I apt-get vegastrike 0.4.3 but vslaunch is nowhere.
I can play the game executing vegastrike but that just drops me in the middle of the game.
I can't also configure the game vsinstall does the same as vegastrike and when i excecute vssetup i get this:



What is happening?

I had this same problem and after several fruitless hours searching for a solution I found it!  This is with the Vega Strike version installed using the Add/Remove Apps via the menu.  What it does is put the setup.config file in /usr/share/games/vegastrike!!!  All you have to do is cd into that dir and run vssetup.  If it complains about not being able to write to setup.config then just chmod 777 it.

After this Vega Strike runs beautifully on my Ubuntu 7.04 Feisty box with P4 2.0mhz, 1g ram, and 256mb ATI Radeon 9550 card.

---

### Post by madsmeg on 2007-10-01
May be 7 months late, but at least we know now :P

---

