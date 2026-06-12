---
title: "Compiz Problems"
date: 2008-03-09
forum: Desktop Environments
---

### Post by buivietkhoa1919upg on 2008-03-09
I use IBM T43 with windows XP installed and i had to install gutsy in vmware workstation, but the compiz didn't work, i found that was because my VGA card is vmware as default, it wasn't ATI X300.

i tried to install compiz to another ibm t43 with ubuntu installed (without windows and vmware) and it worked. 

can i change the default vmware VGA card to my real ATI? have anyone any ideas?

thanks for help

---

### Post by overdrank on 2008-03-09
> **buivietkhoa1919upg said:**
> I use IBM T43 with windows XP installed and i had to install gutsy in vmware workstation, but the compiz didn't work, i found that was because my VGA card is vmware as default, it wasn't ATI X300.

i tried to install compiz to another ibm t43 with ubuntu installed (without windows and vmware) and it worked. 

can i change the default vmware VGA card to my real ATI? have anyone any ideas?

thanks for help

HI and you may find some help here
[http://ubuntuforums.org/showthread.php?t=692556&highlight=vmware](http://ubuntuforums.org/showthread.php?t=692556&highlight=vmware)

---

### Post by buivietkhoa1919upg on 2008-03-09
i didn't find what i need...

a friend of mine said that vmware workstation doesn't support any VGA card, except its own VGA card. but i'm not sure if he was right.

did anyone have the same problem???

---

### Post by mtbsoft on 2008-03-12
VMWare (and most virtual products) emulate a very limited set of certain hardware components (bios, cpu, graphics card, network card, etc.), mapping their functions down to the actual hardware where necessary.

It is therefore not possible to "replace" the graphics card without a rewrite of the emulator.  They have tried to pick middle-of-the-road, generic devices which try to represent a reasonable real world box but this will therefore have limitations, as you have found.

---

### Post by 2vack on 2008-03-12
Hmm.. you could have it the other way around.. Install Ubuntu as your main platform then windows via VM (VM server). Compiz would work but mind you, migrating to ubuntu as your main system is not a walk in the park. 

pero you would get better performance from windows if its virtualized. Mas mabilis ang file system ng ubuntu and having a virtual NTFS drive in there is just amazing. Of course that's just my opinion. 

People are just amazed by how I "flip" from one OS to another.. Ang bangis! :guitar:

---

