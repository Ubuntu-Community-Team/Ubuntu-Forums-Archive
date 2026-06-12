---
title: "Booting problem."
date: 2006-06-26
forum: Desktop Environments
---

### Post by cydec on 2006-06-26
I'm having some troubles booting my system. (Im using Drapper)

At some point my system crashed and i had to use the power button to reboot my system.
After that he loads all modules but when he eventualy tries to open the loginscreen he crashes.
Now i had that before: when I tried to install the CD of drapper i had exactly the same problem (when he goes to the live version).
Now that could solve that by just changing the VGA mode (at the point where i should select "start ubuntu or install") to 1027x768 and then the live cd booted like it should.

Now I'm having the same thing but it is not the cd, it's the installed version.
Maybe there is a way to change the VGA mode ?!

Or is there another solution...

(something i forgot to mention: when he crashes he keeps checking my floppy drive)

---

### Post by cydec on 2006-06-26
is there any way i can change the x vga ?

---

### Post by Sonofmoog on 2006-06-26
You'll need the specs for your monitor and graphics card, so have them handy before you begin.  

1) Run dpkg-reconfigure xserver.xorg
2) Answer the questions with the specs you got from your manuals.
3) Ctrl-Alt-Backspace to kill X

If all went well, the next thing you should see is X restarting as it should

---

