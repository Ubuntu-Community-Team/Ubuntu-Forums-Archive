---
title: "Logitech G15  -  g15composer problem"
date: 2007-12-19
forum: Gaming &amp; Leisure
---

### Post by mback99 on 2007-12-19
My ubuntu system is 7.10

I can't get g15composer to display text on the lcd

This is what I've have done..

sudo modprobe uinput
sudo g15daemon
sudo nohup  g15composer ~/g15lcd &

but when I try

echo 'TL  "hello"'  > ~/g15lcd

nothing is displayed on the lcd...

---

