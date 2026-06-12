---
title: "boot issue"
date: 2009-01-18
forum: General Help
---

### Post by DylanW on 2009-01-18
whenever I boot Grub tries to load kernel 2.6.27-11(8.04 right?) and fails so I've been having to load into 2.6.24-23(8.10?) by hitting escape and manually selecting it from the menu

I went into Synaptic and reinstalled everything that was like linuximage-2.6.27-11 and I still have the problem

idea's?


On a different note, I'm learning Python and C, and am wandering if anyone has a general idea of where I'd start at password protecting an external HD

I was thinking, removing the device from view of windows computers is pretty easy so I could just make it console based

but linux pw protecting gets more complicated, mostly because I've only been using Ubuntu for a year

---

### Post by DylanW on 2009-01-18
*bump*

---

### Post by defishguy on 2009-01-18
You need to edit the Grub menu so that the Kernel you want to use is the default.

The information [**_here_**]("https://help.ubuntu.com/community/GrubHowto") should help you with that.  Please remember to make a backup copy of the list before making any changes.

> cp /boot/grub/menu.lst /boot/grub/menu.lst.old

I can't really help with your other question.  Sorry.

---

### Post by DylanW on 2009-01-18
that's not my problem, my problem is the newer kernel fails to boot, i just get a black screen and a blinking capslock light

---

### Post by DylanW on 2009-01-19
bringing it back from page 9

---

### Post by defishguy on 2009-01-19
Mis-read the original post.  That sounds like a kernel panic.  Check out this thread.  [http://ubuntuforums.org/showthread.php?t=968792]("http://ubuntuforums.org/showthread.php?t=968792")

---

### Post by DylanW on 2009-01-19
thanks, rebooting now to see if that works

---

### Post by DylanW on 2009-01-19
no luck, but i do get an error now

```
[     0.808118] Kernel panic - not syncing: VFS; unable to mount root fs on unknown block(0,0)
```

---

### Post by DylanW on 2009-01-19
if it helps anyone I thought about it and i think this started like a week ago when i was trying to get splashy to work, so i uninstalled usplash, but later i uninstalled splashy and reinstalled usplash because i got tired of messing with it

---

### Post by DylanW on 2009-01-21
I doubt this is related but sometimes when i open my laptop my cd drive opens :-s

---

