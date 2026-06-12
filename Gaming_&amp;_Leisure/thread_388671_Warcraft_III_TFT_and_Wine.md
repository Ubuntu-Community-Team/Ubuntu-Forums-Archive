---
title: "Warcraft III TFT and Wine"
date: 2007-03-19
forum: Gaming &amp; Leisure
---

### Post by PandaGoat on 2007-03-19
I am attempting to find solutions for when windows XP becomes unsupported [I am dual booting for gaming reasons] because I refuse to upgrade to vista.  I installed Warcraft III TFT perfectly; it runs perfectly; the only problem is that my keyboard fails work.  I am running it as so: "wine war3.exe -opengl."  When I run it in terminal everything that I type with Warcraft opened is typed in the terminal. 

Radeon 9600 with the fglrx driver.

O_O Any ideas? 
Thank you.

---

### Post by knickers on 2007-03-26
Pandagoat,

I believe your problem is your wine configuration.

go to your terminal and type

> sudo winecfg

Select the "Graphics" tab, then make sure the "Allow the window manager to manage created window" is checked.

This should fix your problem.

~cheers
~dj

---

