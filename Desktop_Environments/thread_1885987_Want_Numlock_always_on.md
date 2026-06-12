---
title: "Want Numlock always on"
date: 2011-11-24
forum: Desktop Environments
---

### Post by yaweli on 2011-11-24
Hi

How can I make my ubuntu to have the Numlock always on , All the time
no matter what 

(there is a free utility for windows "numlocker")

thanks 

j.r

---

### Post by IanW on 2011-11-24
Numlock is often a BIOS option.

---

### Post by kurt18947 on 2011-11-24
There is an app called 'numlockx' in the repositories.  Install & add to startup applications.  That should do what you want.  I've had 2 Gigabyte MBs that did not have a numlock option in BIOS.

---

### Post by skit85 on 2011-11-25
Ive been wondering the same thing, i dont have the option in BIOS ill look for numlockx hopefully that does the trick :)

Thanks Yawell for starting the thread and thanks kurt18947 for the lead...

---

### Post by yaweli on 2011-11-27
Hi

I need solution to permanently have the numlock = on. 
not the BIOS, not at startup , all the time .
Even if I will press NumLock, it's should stay on.

For now I have written a script which run in loop forever and do this :

[B]#!/bin/sh
while true
do
        sleep 4
        numlockx on
done[/B]

If the keyboard lost the Numlock at any reason , it will restore it in maximum 4 seconds. 

Yaweli.


Still ,  someone know better solution , from inside the Ubuntu keyboard driver 
I will appreciate it.

Regards

---

### Post by underquark on 2011-11-27
I sort-of remember how to do this but you'll need to experiment:

Start with NumLock On

open terminal

```
xev
```press some keys and you will see it show the key number for each (my NumLock key shows as 77).

```
xmodmap -e 'keycode 77 = NoSymbol'
```

Then, if it works, add it to StartUp

---

### Post by yaweli on 2011-11-28
Hi

blocking key 77 disable the the ALT keys for me. I suggest **not** to try it.
it disable the ALT the CTRL and the SHIFTS

yaweli

---

### Post by efball3 on 2011-12-01
> **yaweli said:**
> Hi

blocking key 77 disable the the ALT keys for me. I suggest **not** to try it.
it disable the ALT the CTRL and the SHIFTS

yaweli

You have to get the right keycodes, I remap all the keys in the keypad so they are fixed to what I want and cannot change.

Store your current keymappings for reference:
xmodmap -pke > xmodmap.conf

Get all the keycodes for your keypad keys for your specific computer/keyboard with xev.  Then you need a file with all the new mappings (usually called .Xmodmap). xmodmap is used to remap the keys:

xmodmap .Xmodmap

If the .Xmodmap file is in your home directory gdm may do this automatically for you.  Here are my keycodes for my Dell desktop with a Asus USB keyboard:

cat .Xmodmap

clear Mod2
! Mod2 is NumLock

keycode 87 = KP_1
keycode 88 = KP_2
keycode 89 = KP_3
keycode 83 = KP_4
keycode 84 = KP_5
keycode 85 = KP_6
keycode 79 = KP_7
keycode 80 = KP_8
keycode 81 = KP_9
keycode 90 = KP_0
keycode 91 = KP_Decimal
keycode 106 = KP_Divide
keycode 63  = KP_Multiply
keycode 82  = KP_Subtract
keycode 86  = KP_Add
keycode 108 = KP_Enter

remove Lock = Num_Lock
keycode 77 = comma
! map the NumLock key to whatever you want

By default the keypad keys are mapped to different symbols than the main keyboard keys with the same name.  Some programs treat them the same, some don't.  I map my keypad to use the same symbols as the main keyboard:

clear Mod2
! Mod2 is NumLock

keycode 87 = 1
keycode 88 = 2
keycode 89 = 3
keycode 83 = 4
keycode 84 = 5
keycode 85 = 6
keycode 79 = 7
keycode 80 = 8
keycode 81 = 9
keycode 90 = 0
keycode 91 = period
keycode 106 = slash
keycode 63  = asterisk
keycode 82  = minus
keycode 86  = plus
keycode 108 = Return

remove Lock = Num_Lock
keycode 77 = comma

---

