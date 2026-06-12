---
title: "Boot Gutsy fail"
date: 2008-05-09
forum: Dell Ubuntu Support (CLOSED)
---

### Post by arkadian on 2008-05-09
My first post here, i am Slowly integrating to Linux from windows.
i have a 700m dell with 1.8 cpu and 82852/82855 graphic card.
i installed 7.10 fully updated and then decided to change my driver for the video card from the one linux picked to another one i believe i810 driver. i saved. rebooted and thats it.
i get grub menu, load the kernel.
it hangs or keeps flickering the loading screen where it says something like
....... ok
....... ok
....... ok
....... ok
also i tried to start with the ubuntu cd. works ok able to see my two PARTITION disks (ubuntu and windows xp)
however when i try to go into Screens and Graphics, at that point my mouse, everything freezes.
tired of reformatting and reinstalling ubuntu, need your help my dear linux friends.
if possible to change the graphic driver or delete the configuration SO I can boot into the ubuntu.

thank you

oleg

---

### Post by arkadian on 2008-05-09
I FOUND some interesting issue maybe relevant to mine but i am confused.
run xfix
or
You need to install 915resolution when using "i810" driver to get 1280x800 resolution.
sudo aptitude install 915resolution
or
xorg.conf.gz 

i also found a newer driver from intel but dont know how to install graphic drivers. could this be it: gksu displayconfig-gtk 

oleg

---

### Post by arkadian on 2008-05-09
Any One:( :( :( :( :(

---

### Post by prshah on 2008-05-09
> **arkadian said:**
> the video card from the one linux picked to another one i believe i810 driver. i saved. rebooted and thats it.
oleg

first open a terminal (Applications-Accessories-Terminal) and give the command```
sudo apt-get install xserver-xorg-video-intel

```

Then Alt+F2, ```
gksudo gedit /etc/X11/xorg.conf
```.

In the editor window that opens up, find the line looking like > Driver "i810", and replace the word "i810" with "intel". Save, and close the editor.

Logout, press Ctrl+Alt+BkSp, the screen should flicker and reappear within a few seconds. Now login and try your "Screens and Graphics"; is it OK?

---

### Post by arkadian on 2008-05-11
hey thanks a million, worked like a charm. And was actually fun ;D

on a similar note, will this intel driver do the function it should? for instance if i install a game, or do i need a different driver for such use?
and i believe id need to install some sort of directx.


thanks a lot,

oleg

---

### Post by free2useemail on 2008-05-12
This has happened to me! Be careful when picking a graphic driver in linux, use the one linux set. To fix this, start ubuntu, but once the OS starts, it will say something at the beginning, press ESC right away after bios boot up  to go to a boot screen. In the boot screen, there should be a recovery Opection. Use that! if that does not work, you will have to reinstall. 

Just don't mess with graphic driver unless you are advanced at computers (if you are, then this stuff happens to use all the time)

---

### Post by prshah on 2008-05-13
> **free2useemail said:**
> Use that! if that does not work, you will have to reinstall. 


Just a friendly tip; be sparing with advice on reinstalling ubuntu. Across 30+ machines, over a year of usage, I have never had to re-install ubuntu, even to recover from catastrophic failures such as an interrupted upgrade.

There is definitely no need to re-install over a graphics related issue; and very little call to go into recovery mode, as well.

Your well-meaning advice can actually frighten a person away.

If you are relatively committed to linux, you will also not have to recourse to a reinstallation.

Just a spot of advice; you can use it or ignore it as you see fit.

---

### Post by arkadian on 2008-05-14
thanks everyone, you guys rock!:)

cheers

oleg

---

