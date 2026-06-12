---
title: "bootable usb?"
date: 2009-05-08
forum: General Help
---

### Post by ooobooontooo on 2009-05-08
Hi,

I've been following the instructions from [https://help.ubuntu.com/community/Installation/FromUSBStick]("https://help.ubuntu.com/community/Installation/FromUSBStick"). I did the things it told me to do there, but now I'm at a loss. Am I supposed to go into the grub menu and boot the usb from there or is it supposed to just automatically boot like it does for the live cd? Is there a sort of BIOS that I can go into to change the boot order and stuff? Thanks in advance.

---

### Post by nothingspecial on 2009-05-08
There will be an option in your bios to boot from usb.

---

### Post by Peter09 on 2009-05-08
As a quirk, my BIOS shows no options for USB, but when a bootable USB is inserted at boot time it will ask if it should be the boot media.

---

### Post by ooobooontooo on 2009-05-08
@ nothingspecial
I agree...how do I get there...for ubuntu is it just grub?

---

### Post by nothingspecial on 2009-05-08
Before you reach grub, just after the computer starts you will have to press one of the F buttons or Escape which should bring you to the bios menu. From there you should be able to find your boot settings.

If the screen doesn`t tell you which button to press then the instruction manual will. If you don`t have the manual then you will have to experiment or use google.

A word of warning, don`t forget to change the settings back. One of my laptops won`t boot if there is a usb drive plugged in and the bios are set to boot from usbhdd first. Doesn`t happen with any other box of mine though.

---

### Post by ooobooontooo on 2009-05-08
@ nothingspecial
Thanks wasn't sure if BIOS was os dependent

EDIT: Nevermind...I'm fine for now. Thanks to pastalavista and Peter09 for responding.

---

### Post by pastalavista on 2009-05-08
At the first boot screen BEFORE grub loads, where it shows the branding of the computer or the motherboard, hit a special key wwhich is different for different PCs. It should say on the screen somewhere something like "Press F2 to enter Setup" (what it says on my Acer screen... may be different on yours). Then put USB in the boot order ahead of the hard drive.

---

### Post by ooobooontooo on 2009-05-08
Hi,

Now I have a new question. I've successfully gotten the computer to boot from the usb. Now I get on to the same menu as I would for the live cd, but when I click either "try kubuntu without changing your computer" or "check cd for corruptions", the screen just stalls and doesn't do anything (It might be that I'm too impatient and I didn't wait long enough of course,but I gave it a good 2 minutes or so). I did see a lot of activity going on with the usb (the light was flickering anyway)....but still I didn't see any changes to the screen. Also, when I try to "load from the first hard disk", it keeps going back to boot from the usb. Can anyone explain the behaviors exhibited? Thanks in advance.

---

