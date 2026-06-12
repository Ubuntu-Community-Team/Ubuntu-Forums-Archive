---
title: "A very, very basic Nessus question for a newbie!"
date: 2006-02-21
forum: Desktop Environments
---

### Post by jimwillsher on 2006-02-21
Oops sorry, wrong forum (should be breezy).




Help! I'm embarrassed asking this, but here goes...

I have Ubuntu running as a server, all well and good. Tonight I've taken the bold step of installing Ubuntu as a desktop version too. Woohoo!

Anyway, I want to play with Nessus (primarily, to scan my Ubuntu server!). I've installed nessusd and nessus-client via synaptic, and they are installed successfully. Versions 2.x from the apt repositories.

But....now what! How do I actually get into the Nessus application, to configure it and run it.

How embarrasing...


I'm on Breezy, with the "default" install (gnome).

Many thanks!

:confused: Jim

---

### Post by Marcos.Rufino on 2006-03-15
Open a terminal and type:

> sudo nessusd 

This will run the nessus server. After that, type:

> sudo nessus

And voilá!

---

