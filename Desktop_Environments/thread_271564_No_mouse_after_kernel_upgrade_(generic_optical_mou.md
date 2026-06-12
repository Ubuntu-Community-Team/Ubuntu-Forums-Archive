---
title: "No mouse after kernel upgrade (generic optical mouse)"
date: 2006-10-04
forum: Desktop Environments
---

### Post by odiseo77 on 2006-10-04
Hi people. This is the first problem I come across with Ubuntu after I started using it when Dapper was released. I bought a new PC last week and installed Ubuntu Dapper (6.06) in it. After the installation I proceeded to update my system and to my surprise, when I booted the new kernel (2.6.15-27-386), I got absolutely no response from the mouse movements, so I got stucked in GDM and had to go to a virtual console with ctrl-alt-f1 to reboot the system (the keyboard did work well). So now I must always boot the Ubuntu default kernel (2.6.15-23-386). 

My mouse is a generic, wired and optical one that came in a "3 in 1 combo" (a box with a mouse, a keyboard and a couple of speakers). It has no trade mark, only says "Made in China", and has a model number (GM-728 ). 

Does anyone know what might be the problem? Could a next kernel update fix it, or will I have to change my mouse?

As a side note, the mouse works fine on Elive (another distro I installed in this computer; kernel 2.6.15).

Thanks in advance.

---

### Post by reclusivemonkey on 2006-10-05
> **odiseo77 said:**
> 

Does anyone know what might be the problem? Could a next kernel update fix it, or will I have to change my mouse?

As a side note, the mouse works fine on Elive (another distro I installed in this computer; kernel 2.6.15).

Thanks in advance.


The relevant section of your Xorg.conf would help in diagnosing the problem...

---

### Post by odiseo77 on 2006-10-05
Hi reclusivemonkey, here's the mouse section of the xorg.conf file:

```
Section "InputDevice"
        Identifier      "Configured Mouse"
        Driver          "mouse"
        Option          "CorePointer"
        Option          "Device"                "/dev/input/mice"
        Option          "Protocol"              "ExplorerPS/2"
        Option          "ZAxisMapping"          "4 5"
        Option          "Emulate3Buttons"       "true"
EndSection
```

Everything looks fine to me. Besides, the mouse works perfect on ubuntu's default kernel which is the one I'm using now (2.6.15-23-386).

Any suggestion??

Thanks in advance.

---

