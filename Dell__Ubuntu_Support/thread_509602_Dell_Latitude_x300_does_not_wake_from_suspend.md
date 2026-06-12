---
title: "Dell Latitude x300 does not wake from suspend"
date: 2007-07-25
forum: Dell  Ubuntu Support
---

### Post by Frogger on 2007-07-25
I just installed Feisty on a Dell Latitude x300.

Out of the box, suspend and resume work under Mandriva, but with Ubuntu it does not.

When I try to resume, it goes through the motions to resume, but the screen stays blank (but it does turn on).

Anyone have any ideas?

---

### Post by strabes on 2007-07-25
See the link in my profile.

---

### Post by carac on 2007-10-16
It might be a problem with bcm43xx - with 7.10 RC I had similar problems but after blacklisting bcm43xx and installing ndiswrapper it seems that it works OK (except when called on lid close, which seems to be a different script or something).

---

### Post by derred on 2007-10-24
The problem is with the new intel video driver. You have to use the older driver (i810) and everything works great. Just replace like the driver option in device section:

Section "Device"
        Identifier      "LEAVE YOUR ADAPTER NAME"
#driver intel does not work with sleep
#       Driver          "intel"
        Driver          "i810"
        BusID           "LEAVE YOUR BUS ALONE"
EndSection

---

### Post by mwob on 2008-02-06
Hi, I have the same probem - hibernate and standby won't resume, they just die.

Can anyone elaborate on the previous instructions - do I need to change a file somewhere to change driver or do I need to blacklist something (does anyone know what I need to bloacklist?)

I'm using compiz, but with that turned off I still have the same issues...

Thanks all.

---

### Post by Cr0wley on 2008-02-20
Try;
System, Administration, Screens and Graphics
Enter your password then go to the 'Graphics Card' tab
Click where it currently says 'intel - experimental...' then again on the top line next to 'choose driver by name'
Select 'i810 - Intel Integrated Graphics' then click Ok twice to get back to the desktop

That's how I interpreted the change, but I am new to this m'larky so there might be a better way. I'll find out if it works soon ;)

Edit: Gutsy didn't like that :( Instead of using 'choose driver by name' use 'choose driver by model' then select Intel and 810

---

