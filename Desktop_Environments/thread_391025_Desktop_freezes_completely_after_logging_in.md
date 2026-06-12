---
title: "Desktop freezes completely after logging in"
date: 2007-03-22
forum: Desktop Environments
---

### Post by fracktor on 2007-03-22
When logging into my desktop it completely freezes after a ceartin point. Its usually right after all the icons appear on my desktop. Sometimes I am able to quickly open up a terminal or other application but by the time it opens, everything freezes, no errors. I get no response from the keyboard or the mouse. ctrl alt backspace doesn't work, I have to power off the pc. I am able to login to any other account fine. The only thing I installed recently was NVU - a html authoring program.

So far I tried  dpkg-reconfigure xserver-xorg

aptitude install ubuntu-minimal
aptitude install ubuntu-base
aptitude install xserver-xorg x-window-system-core ubuntu-desktop

aptitude update
aptitude upgrade
aptitude dist-upgrade

---

### Post by fracktor on 2007-03-23
Anyone have any ideas?

---

