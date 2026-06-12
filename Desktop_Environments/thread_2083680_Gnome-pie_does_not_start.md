---
title: "Gnome-pie does not start"
date: 2012-11-13
forum: Desktop Environments
---

### Post by alvpizz on 2012-11-13
hello :) ! I am running ubuntu 12.10 on a Samsung RC530. my recent problem is that gnome-pie does not work anymore. o would like to have it back, because it was very comfortable to me.
if i launch it from the terminal, i get this mistake: 
[MESSAGE] Welcome to Gnome-Pie 0.5.3!
[MESSAGE] Loading Pies from "/home/alvise/.config/gnome-pie/pies.conf".
[MESSAGE] Started happily...
Errore di segmentazione (core dump creato) [translated: "segmentation error (core dump created)"

how can i solve this?

---

### Post by ibjsb4 on 2012-11-13
Should of worked; try reinstalling it.

sudo apt-get remove --purge gnome-pie && sudo apt-get install gnome-pie

---

### Post by alvpizz on 2012-11-13
> **ibjsb4 said:**
> Should of worked; try reinstalling it.

sudo apt-get remove --purge gnome-pie && sudo apt-get install gnome-pie

tryied.. but when i start it again i get the same error message. thanks anyway.

(obviusly, previusly gnome-pie worked)

---

### Post by ercherramon on 2012-11-13
you may have a theme or icon pack that does not support the version of gnome-pie installed.

---

### Post by alvpizz on 2012-11-13
> **ercherramon said:**
> you may have a theme or icon pack that does not support the version of gnome-pie installed.

ok i'll try to solve it. thanks!

---

### Post by alvpizz on 2012-11-14
gnome-pie is still not working! 
these are the theme settings I'm using. there should be nothing wrong..

---

### Post by ibjsb4 on 2012-11-14
Im not finding any reports of breakage; just yours.  Maybe its time to ask Simon.

[https://launchpad.net/~simonschneegans/+archive/testing?field.series_filter=quantal](https://launchpad.net/~simonschneegans/+archive/testing?field.series_filter=quantal)

---

### Post by alvpizz on 2012-12-02
i had re-installed my ubuntu-pc to overcome the problem.. and just now it is happened again. i have started the computer, and unexpectedly i have fount the message "gnome-pie has unexpectedly crashed". and now i can't start it anymore. i have installed only faenza-icon-theme, so I don't think i have installed some icons which are not supported by gnome-pie. what shall I do?

---

