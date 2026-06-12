---
title: "Cannot Open Display"
date: 2009-03-29
forum: General Help
---

### Post by LaptopU on 2009-03-29
Hi all,

This is driving me nuts!!

Get 'cannot open display' for EVERYTHING when I'm using a hotel WiFi connection.  If I disable the network I can launch a program, I can browse, use Pidgin etc., but can't launch a single thing.

This isn't a problem when I'm at home on either a wired or wireless network.  Using Intrepid here.  Please, please any help is appreciated and if you can solve this one I'll be in awe forever!

---

### Post by LaptopU on 2009-03-31
There has been a development in this, and it's permission based.

If I open a terminal and type "xhost +local:" I have absolutely no problems.

How can I edit my config files to allow this automatically on boot, and has anyone an idea what would cause this in the first place?  Anything I can edit in GDM?

Thanks in advance, this problem has been going on for what seems like forever and I'll be glad once it is fixed.

---

### Post by 123456789123456789123456 on 2009-03-31
Is the wifi connection you usually connect to protected, or unprotected.  If it is a hotel, the connection is probably unprotected.  I am assuming that if it is protected from the normal use, then over time, it has gotten used to this setting, and needs to be told to except the other unsecured network.

Try under connections, to have the computer accept this connection.  That should tell it to allways trust the connection, and you should not have any problems.  However, I have to admit, I have not run into this type of problem before

---

### Post by LaptopU on 2009-03-31
It's a Radisson hotel which uses an unsecured network.  The procedure is WiFi connects to the network, then browsing is not permitted until a browser is launched which brings up a simple login screen which I have to click 'login' before any sort of internet connection is permitted.  After I have done this I can browse, use Pidgin etc., but if I want to launch any program when logged on I must use the command "xhost +local:".

It's taken me several weeks to work this out, so you can imagine how frustrated I've been with it.  I'm not intending to use another hotel soon as this is a corporate venue my company uses, so can't test the setup to see if it's across the board.  I don't want to add a rule just for this hotel though to be honest, a Windows machine would handle the situation absolutely fine, it seems completely bizarre an Ubuntu machine cannot.

---

