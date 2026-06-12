---
title: "Dual display, dim laptop lcd"
date: 2009-01-05
forum: General Help
---

### Post by mike.dh.mount on 2009-01-05
Hey all,

Having a problem with dual display on a toshiba m200. At home I can plug my Dell LCD into the vga port and everything works great, but at work I have a dell CRT and if I plug that in, both displays work, but the laptop is very dim. I have tried the FN keys to adjust the brightness as well as checked my power management settings. I am using 8.04, running xfce. Any thoughts?

---

### Post by rlong on 2009-03-08
I'm having the same problem with kubuntu 8.04 on a Toshiba Tecra M3. Have you solved this? I'll let you know what I discover.

---

### Post by rlong on 2009-03-08
The problem is that the backlight in these Toshiba laptops doesn't come on if another display is plugged in when X starts. I was able to turn it on manually using the toshset utility as follows:

```
sudo apt-get install toshset
sudo toshset -bl on
```

I hope this was helpful.

---

