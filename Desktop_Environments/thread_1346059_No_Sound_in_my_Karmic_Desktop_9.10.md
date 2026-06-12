---
title: "No Sound in my Karmic Desktop 9.10"
date: 2009-12-04
forum: Desktop Environments
---

### Post by mhmmm on 2009-12-04
Hi
How are you?

I was asking about the karmic (9.10) in my Toshiba Satellite Pro Laptop.
After I installed the OS, the sound was working then the sound after I installed few programs ===) no sound appear.

thanks
:p

---

### Post by ram2500 on 2009-12-04
What programs did you install? (name, version, what it does [for those who might not be familiar with its function])

I think, but I'm not sure, if you installed another sound-mixing app, you MIGHT have overridden the one that came with Ubuntu, but I'm not exactly sure. 

Try uninstalling the programs until you have nothing but the defaults, and then install one program, see if the sound works, etc until you install a program and the sound doesn't work. The program installed before the sound didn't work would be the culprit.

---

### Post by akashiraffee on 2009-12-04
There's a four page thread somewhere else in here about no sound on KK -- I bet if you go to Preferences->Sound System, you will get an eternal "Waiting for Sound System to Respond" message.  

[http://ubuntuforums.org/showthread.php?t=1312624](http://ubuntuforums.org/showthread.php?t=1312624)

A bunch of different suggestions are there.  None of them worked for me, but I haven't tried them all yet either.  Also, rebuilding the kernel may help -- right now "lsmod" shows modules loaded for the onboard video and sound, neither of which are in use.   Building your own kernel can alleviate conflicts like that.

The "sound system" is traditionally the most dsyfunctional part of linux, ever since I can remember.

---

### Post by mhmmm on 2009-12-05
my problem is treated by opening the terminal and typing [COLOR=Red]"[/COLOR]  [FONT=&quot][COLOR=Red]sudo alsa force-reload"[/COLOR]
but I should do this code every time I open the computer
Does there any one know any permanent solution?
thanks
[/FONT]

---

### Post by mhmmm on 2009-12-05
what does this  [COLOR=#ff0000]"[/COLOR] [FONT=&quot][COLOR=red]sudo alsa force-reload"   [/COLOR][/FONT] do?
and why it's temporary & it's ended after I close my computer
I need permenant solution.
thanks
 
How can I put this   [COLOR=#ff0000]"[/COLOR] [FONT=&quot][COLOR=red]sudo alsa force-reload"  in terminal [/COLOR][COLOR=#000000]in the startup?[/COLOR][/FONT]
 
thanks

---

