---
title: "Battery monitor / charge level indicator"
date: 2013-08-06
forum: Desktop Environments
---

### Post by dminuth on 2013-08-06
Hi, first time post.
Hardware is a toshiba satellite l745d laptop.  Software is Ubuntu 12.04 x64 unity WM.  For some reason i am not getting any indication as to wether i am running on battery or if plugged in.  I have tried different "Battery Monitors" and even those do not show anything but 0% charge.  I know that the battery works since i am typing this while on battery, but it seems i am not getting any reading from the battery at all..

i have tried using the terminal ang using " acpi -b "  it gives me absolutely no output.

does anyone have an idea as to what i am overlooking or missing.

---

### Post by dminuth on 2013-08-07
ok, i have figured out that it is the toshiba-acpi kernel module that is not loaded.  When i do sudo modprobe toshiba-acpi, i get no return and nothing seems to happen anywhere.  So what do i need to do to load this module ?

---

### Post by PopsTheSailor on 2013-11-13
I'm having the same problem. Anyone figure out how to get battery monitoring working on a Tosh#$ba?

I've had nothing but issues with Toshiba's running Ubuntu. I'll never buy one again.

---

### Post by 3rdalbum on 2013-11-13
> **pops2 said:**
> I'm having the same problem. Anyone figure out how to get battery monitoring working on a Tosh#$ba?

Not all computers with the Toshiba brand-name have the same components in them, you know. You'd have more luck stating the model number.

Also, have you tried with the latest Ubuntu? Newer Ubuntu == Newer drivers.

---

### Post by PopsTheSailor on 2013-11-13
I'm using a toshiba satellite L655-s5150 with Ubuntu 13.04.

I've fought wifi issues with thing literally for several years now. Wifi worked great on 11.04 but when 12.n came along, problems, problems, problems. After many months and attempts to solve it, I finally found something on a German website that has fixed it (knock on wood) but that's a different story for a different thread. I just know that my future laptops will NEVER be Toshiba again.

---

