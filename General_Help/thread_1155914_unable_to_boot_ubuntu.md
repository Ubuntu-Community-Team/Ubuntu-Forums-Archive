---
title: "unable to boot ubuntu"
date: 2009-05-11
forum: General Help
---

### Post by muctadir on 2009-05-11
i am using dual boot of ubuntu and windows.
after re-setup my windows, ubuntu is not showing in the bios menu.

need help.
what can i do???

---

### Post by suhanduman on 2009-05-11
[http://www.howtogeek.com/howto/ubuntu/reinstall-ubuntu-grub-bootloader-after-windows-wipes-it-out/](http://www.howtogeek.com/howto/ubuntu/reinstall-ubuntu-grub-bootloader-after-windows-wipes-it-out/)

---

### Post by pro003 on 2009-05-11
it's because you did repair your windows installation, that overwrote the grub, now you need to restore grub by doing repair on ubuntu and you can chose repair or fix at installation menu, you should see somewhere "restore grub" or something like that....

---

### Post by jee_bee on 2009-05-11
[COLOR="DarkRed"]U need to reload grub boot loader. When u ave instal XP ,,  the xp boot loader put is self in front of grub boot loader [/COLOR]



[COLOR="blue"]First step-[/COLOR]  boot Ubuntu using the Ubuntu cd/dvd on the option LIVE CD ( The option name is  "Try ubuntu whitout any modification to your system")

[COLOR="Blue"]second step-- [/COLOR]Open a Terminal.....

[COLOR="blue"]third step---[/COLOR] Type in "sudo grub" [COLOR="DarkRed"]press enter[/COLOR]
              Type in "find /boot/grub/stage1" [COLOR="darkred"]press enter[/COLOR]
          (This will return a location  ex  [COLOR="Yellow"](hd0,1))[/COLOR]             \|/ U will need that info here \|/
              Type in "root (hd?,?)" [COLOR="darkred"]press enter[/COLOR]
              Type in "setup (hd0)" [COLOR="darkred"]press enter[/COLOR]
              Type in "quit" [COLOR="darkred"]press enter[/COLOR]


[COLOR="blue"]fourth step----[/COLOR] Reboot... don't forget to remove the cd from your cd drive !!!!

[COLOR="Red"]Thats it your done !!!!!!!!!![/COLOR]

This is supose to be easy like 123 but sometime some machine
are setuped in bizare way... let me now if u ave any trouble !!!

Peace !! And ave a good Ubuday !!!!

---

