---
title: "Stop Ubuntu Session items starting in KDE"
date: 2009-02-06
forum: General Help
---

### Post by blazemore on 2009-02-06
How do I prevent stuff like Gnome-Do (Which I have under Gnome) from appearing at startup in KDE4?

---

### Post by cariboo on 2009-02-06
You can't without removing it from your home directory. I would suggest creating another user if you want to run a strictly kde session.

Jim

---

### Post by The Recorder on 2009-02-06
Go to "/home/*your name*/.config/autostart".
Find the "???.desktop" file for the item that you want to control (e.g. Gnome-Do).
Open this file in a text editor.
Add the following line at the end of the file, and save:
   OnlyShowIn=GNOME (or,for example, OnlyShowIn=GNOME;XFCE) (USE UPPER AND LOWER CASE LETTERS THE WAY SHOWN!!!)

You can use this method to control any item from GNOME, KDE, or XFCE.

Good luck!

---

