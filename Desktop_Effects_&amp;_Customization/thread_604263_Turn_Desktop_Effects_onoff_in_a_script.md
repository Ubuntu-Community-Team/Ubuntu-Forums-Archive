---
title: "Turn Desktop Effects on/off in a script"
date: 2007-11-05
forum: Desktop Effects &amp; Customization
---

### Post by rohan000 on 2007-11-05
Some programs don't run when desktop effects are enabled. So, I want to make a script to turn them off, run the program, then restart desktop effects when it's closed. How do I do this in Gutsy?

---

### Post by smartboyathome on 2007-11-06
You should be able to create a launcher up on the top bar that has a command like this:
metacity --replace | programcommandhere | compiz --replace
This should run metacity --replace (the default Window Manager for GNOME), then run your program, then turn Compiz back on (the window manager that provides desktop effects) when the game finishes running (this normally happens when you close the game, but in some rare cases it happens before, in which case it may freeze your computer).

---

### Post by rohan000 on 2007-11-06
When I do that it turns Compiz back on immediately after the program starts, rather than after it closes. Is there a way to make it stop until the program is closed?

---

### Post by evilgold on 2008-01-12
> **rohan000 said:**
> When I do that it turns Compiz back on immediately after the program starts, rather than after it closes. Is there a way to make it stop until the program is closed?

try using && instead of |

---

### Post by gupta_sumesh63 on 2008-01-14
Theres a .deb available called compiz-switch. Google for it. You can switch compiz on an off with one mouse click. Once downloaded and installed its available in applications->Accessories. Add it to the panel. I am attaching the deb if you need it.
cheers

---

### Post by Forlong on 2008-01-14
You don't need to google for it: [http://ubuntuforums.org/showthread.php?t=662926](http://ubuntuforums.org/showthread.php?t=662926) :)

---

### Post by tszanon on 2008-01-14
In Feisty, you can install gnome-compiz-manager and use its tray icon to turn compiz on or off.
Probably there's something like it for Gutsy too.

---

### Post by PhrankDaChickenGeek on 2008-01-14
> **rohan000 said:**
> Some programs don't run when desktop effects are enabled. So, I want to make a script to turn them off, run the program, then restart desktop effects when it's closed. How do I do this in Gutsy?

Yeah, I had the same problem - so I made this: [http://ubuntu.online02.com/nocompiz](http://ubuntu.online02.com/nocompiz)

---

