---
title: "STartmenu!"
date: 2006-01-19
forum: General Help
---

### Post by KhanArash on 2006-01-19
When I restart my computer it comes up a GUI menu which is counting down, and I have to choose between my operativ systems! 

I would ask u if u knew how I could stop it counting down?!

---

### Post by Kiwinote on 2006-01-19
Open the file /boot/grub/menu.lst

Scroll down until you find this:
## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout		10

Change the number after timeout to a higher number

Save

Reboot


Kiwinote

---

### Post by KhanArash on 2006-01-19
THanks...and do you know how I can make for example windows to be first in the list and ubuntu last?

---

### Post by Kiwinote on 2006-01-19
[QUOTE=KhanArash]THanks...and do you know how I can make for example windows to be first in the list and ubuntu last?[/QUOTE]
No I don't, sorry. #EDIT I'm working on something now

Kiwinote

---

### Post by Kiwinote on 2006-01-19
```
sudo gedit /boot/grub/menu.lst
```

Cut this part:
[I]# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hda1
title		Windows 95/98/Me
root		(hd0,0)
savedefault
makeactive
chainloader	+1[/I]

And paste it just above this part:
[I]title		Ubuntu, kernel 2.6.12-10-386 
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.12-10-386 root=/dev/hda2 ro quiet splash
initrd		/boot/initrd.img-2.6.12-10-386
savedefault
boot[/I]

Hope it works, it did on my machine

    Kiwinote

---

### Post by pbb on 2006-01-19
You might also want to know about this one:

Search for the "default" item in /boot/grub/menu.lst, and change the value of it into "saved". That way, it will remember the choice you made previous time, and boot with that one.

---

### Post by KhanArash on 2006-01-19
thanks...do u also know how to change it in kubuntu?!because sudo gedit doesnt woork there

---

### Post by tmahmood on 2006-01-19
just replace gedit with kate

```
sudo kate /boot/grub/menu.lst
```

---

