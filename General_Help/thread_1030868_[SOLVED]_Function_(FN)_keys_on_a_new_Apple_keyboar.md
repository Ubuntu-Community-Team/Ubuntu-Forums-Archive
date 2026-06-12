---
title: "[SOLVED] Function (FN) keys on a new Apple keyboard to work in Ubuntu"
date: 2009-01-04
forum: General Help
---

### Post by k_aneda on 2009-01-04
Posting this here to help out anyone else that's had issues.

With Apple keyboards, by default Ubuntu will assume the "special" function of those keys is enabled (i.e. brightness control, etc.).

Normally you'd have to hit Fn and F5 to refresh in Firefox.

If you wish to revert this behaviour:

> * /sys/module/hid/parameters/pb_fnmode - set that to 2
* must add "option hid pb_fnmode=2" in /etc/modprobe.d/options
* THEN you must regenerate initrd (update-initramfs -u)


Confirmed as working on Ubuntu 8.10 AMD64 with a wired Apple keyboard, should work also for the Bluetooth kbd.

---

### Post by Dj TweeX on 2009-02-12
I just bought an Alu Apple BT keyboard & this wasnt happening for me. how do i set it up to where i can use those fn keys??

---

### Post by k_aneda on 2009-02-15
> **Dj TweeX said:**
> I just bought an Alu Apple BT keyboard & this wasnt happening for me. how do i set it up to where i can use those fn keys??

So if you try:
1. sudo /bin/bash
2. echo 2 > /sys/module/hid/parameters/pb_fnmode

FN keys still don't work at all unless you hold down the FN key?

---

### Post by Dj TweeX on 2009-02-23
they dont work period. the ones on my laptop keyboard work fine. but not the BT keyboard. it appears the fn key does nothing. 
tried the code & still nothing

---

### Post by Oliver_U on 2009-03-04
> **Dj TweeX said:**
> they dont work period. the ones on my laptop keyboard work fine. but not the BT keyboard. it appears the fn key does nothing. 
tried the code & still nothing

I have the same problem and would love a solution! I am desperately missing being able to do Fn+Arrow for pgup, pgdown, home, end aswell as Fn+Delete for del. They worked in Hardy, but stopped working in Ibex. I've tried all different apple keyboard layouts, but neither bring this functionality back.

---

### Post by radixor on 2009-12-14
Does anyone know if this has been solved or is this issue still not resolved? Would appreciate any new insights.

Radixor

---

