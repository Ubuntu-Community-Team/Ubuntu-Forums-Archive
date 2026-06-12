---
title: "can't get ati x1500 working with ubuntu"
date: 2008-03-08
forum: Desktop Effects &amp; Customization
---

### Post by steve51184 on 2008-03-08
I've been using windows and linux for years and have upgraded my old nvidia fx 5500 to a ati x1550 for a little gaming on windows and some cool affects with beryl/compz on linux but I've found out that ati don't offer drivers for the x1550 model for linux (unless I'm missing something) so how do i get 3d effects in linux with this card?

---

### Post by boeing777 on 2008-03-08
did you enable restricted driver??

---

### Post by steve51184 on 2008-03-08
yes but i still can't enable 3d effects

---

### Post by boeing777 on 2008-03-08
System --> Adminstration --> Software Sources

Under "ubuntu software" tab check all the check boxes

Under "updates" tab, check all the check boxes

try to enable compiz and see what happens

---

### Post by steve51184 on 2008-03-08
i wasn't trying atm to get compiz installed/working as i need to setup my gfx card first and i was trying the 3d option in the customize page

---

### Post by boeing777 on 2008-03-08
sudo apt-get install xorg-driver-fglrx
sudo aticonfig --initial --overlay-type=X

reboot

---

