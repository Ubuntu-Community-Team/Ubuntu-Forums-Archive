---
title: "Can't load Gnome or KDE? try the acpi=off workaround"
date: 2008-12-18
forum: General Help
---

### Post by nood1e on 2008-12-18
In my own experience i hassled with this problem for weeks. i noticed a BIOS error during boot that showed a BIOS error involving the ACPI function. then my computer would restart right before the GUI loaded or it would glitch with a lot of colored squares and freeze my whole computer. 

i guess ACPI just doesnt work with linux on some boards. my board's bios hasn't been updated by HP since 2006 so im stuck with the original, which also doesn't have any options to control my ACPI. im sure if i were able to use a newer BIOS it would clear up the problem...but i can't. 

so, i installed ubuntu a few times and had no luck with any distro i tried (ubuntu7.04, 7.10, 8.04, 8.10, studio, kubuntu...32 bit or 64 bit releases...nothing worked). i was also using DVD's instead of CD's, which is a no no apparently if you want to boot off of it easily. CD's are the way to go if you are using the standard ISO image. 

so, for anyone in the same boat as me, this is what i did to fix the problem:


-[COLOR="Red"]RE-DOWNLOADED[/COLOR] ubuntu 8.10 CD ISO image

-burned it to a CD (*instead of a DVD like i had been doing*)

-burned it using a newer burner, burning at 24x (*i know they say 4x, but this worked*)

-burnt it using Nero6 on windows xp laptop

-chose the [COLOR="Red"]install[/COLOR] option (*hitting [COLOR="Red"]F6[/COLOR] and choosing the [COLOR="Red"]acpi=off[/COLOR] peramiter before hitting enter to access the install*)

-doing a [COLOR="Red"]full drive[/COLOR] install

-when it reboots after the install hit [COLOR="Red"]ESC[/COLOR] at the GRUB before it loads

-type [COLOR="Red"]E[/COLOR] on the top most option, the general boot thing

-then go to the line that starts with KERNEL and hit [COLOR="Red"]E[/COLOR]

-type [COLOR="Red"]acpi=off[/COLOR] at the end, leaving a space between the last entry and [COLOR="Red"]acpi=off[/COLOR]

-hit [COLOR="Red"]enter[/COLOR] and then hit [COLOR="Red"]B[/COLOR] to boot

-once you are booted type this in the terminal (*to make the acpi=off change permanent, otherwise you will have to enter this at the boot every time*)
```
gksudo gedit /boot/grub/menu.lst
```
(if you get a blank screen in the editor then you entered the path wrong...happened to me. :P )


-find the line that says
```
# defoptions=quiet splash
```

-and make it look like this
```
# defoptions=quiet splash acpi=off
```

-now save it by hitting the [COLOR="Red"]save[/COLOR] button at the top and close it. 

-now type this into the terminal:
```
sudo update-grub
```

-restart, cross your fingers and let ubuntu start up as normal and you shoule be cool.[/SIZE]

this is tested and working on Ubuntu 8.10 only as of right now, just so you know. i said i tried several distros but i only tried THIS exact method on 8.10. 

good luck and happy linux...ing.

:)

---

