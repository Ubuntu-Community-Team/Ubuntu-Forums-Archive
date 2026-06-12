---
title: "[SOLVED] KDE to blackbox transition"
date: 2008-11-30
forum: Desktop Environments
---

### Post by mossman44 on 2008-11-30
I'm running kubuntu 8.04 on an old gateway laptop. It runs sluggish with KDE so I installed blackbox to make it run faster. However, the blackbox menu that appears when I right click doesn't show any of my applications. I can only open xterm or restart from the menu. How to I make all of my applications from my KDE menu appear in the blackbox menu?

---

### Post by Kinetic Being on 2008-11-30
There is a text config file for the menu probably somewhere in /home/your-user/.blackbox

I've never used blackbox on linux, but I know openbox has a package called "obmenu" that really easily configures the menu.

edit: just so you know, blackbox has been shut down for a few years now. All the active blackbox-esque window managers are basically forks like fluxbox, openbox, xoblite, bblean, etc. (the last two are, or were, Windows shells)

---

### Post by mossman44 on 2008-11-30
Thanks for the information. I'll try openbox and see if I can figure it out.

---

### Post by mossman44 on 2008-12-04
I installed openbox but none of my applications appear on the right-click menu. I guess I'm asking how to import the applications menu from KDE to openbox, or any other desktop environment for that matter.

---

### Post by anthro398 on 2008-12-04
As I recall, the last time I used openbox I had to do a lot of manual menu configuration, but it was very simple after looking at the existing XML in the menu.  Oh, and +1 openbox.  Excellent lightweight desktop.

---

### Post by mikjp on 2008-12-05
Urukrama  has a nice openbox tutorial, it might be helpful.

[http://urukrama.wordpress.com/openbox-guide/](http://urukrama.wordpress.com/openbox-guide/)

---

### Post by snowpine on 2008-12-05
sudo apt-get install menu

Then, if necessary, add this line to your ~/.config/openbox/menu.xml file:

<menu id="Debian" />

---

### Post by mossman44 on 2008-12-05
Thank you snowpine, your method worked. I appreciate everyone's help. I love using linux and you guys make the transition from windows to linux a lot easier.

---

