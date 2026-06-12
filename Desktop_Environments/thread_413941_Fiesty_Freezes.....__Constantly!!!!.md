---
title: "Fiesty Freezes.....  Constantly!!!!"
date: 2007-04-19
forum: Desktop Environments
---

### Post by PowerPLay on 2007-04-19
What the hell.... 

Very Frustrated.


Ok Here's what i got:

Ubuntu Feisty Installed on a Gateway 8510GZ.

Whats running you ask...

Avant window Navigator (I think this is the culprit)
Desktop effects
Gaim
Firefox
Thinderbird


My Problem is that it will just complete freeze. I cant use any keyboard emergency shortcuts the computer is completely unresponsive. The only thing i can do is a hard shutdown where i hold the power button. There is no crash manager when i boot it back up and everything seems to run fine until it just freezes again. The only thing i can think of is the desktop effects and AWN. One of the two is screwing up the entire system. My next step is to uninstall AWN all together and see if that makes a difference. (I think i might replace it with Kiba.) I might fresh install and see if it will freeze just running off of a bare install. 

It only seems to do it when i minimize or maximize a window, I think.

Is anybody else having issues like this (relation to AWN or not)?

-PP(TM)

---

### Post by linuxaz on 2007-04-19
Hello,
You may try adding these lines to the grub boot line....
noapic, force acpi, no irq

This works for me on my Laptop & SuSE.

linuxaz

---

### Post by mtwin2 on 2007-04-19
I'm having the same issue where my system appears to be freezing at random.  I just installed some available updates, not sure if they will fix the issue.  Also I'm not using the desktop effects.

---

### Post by PowerPLay on 2007-04-19
ok what about Avant Window Navigator? Are you using it?


-PP(TM)

---

### Post by RedPeasant on 2007-04-20
I'm having the same issue on my Inspiron 4150. I haven't noticed a real pattern for when it does it, but it has done it both in Gnome and when I booted recovery mode to install updates. Sometimes it freezes at the login screen, or it will let me work for a couple minutes before freezing, but it doesn't respond to keyboard shortcuts, and hitting Caps lock doesn't turn the indicator LED on or off. The only way to fix it is to do a hard reboot with the power button. Any suggestions? The system was fine under 6.10. I upgraded last night and it's been freezing all day.

---

### Post by snailian on 2007-04-20
Do any of you have an ATI card installed? 
My nVidia card is being repaired/replaced, so I popped in an old ATI card I had laying around. 
I upgraded to Feisty and was getting freezes until I installed the drivers from ATI. 
It seemed to fix the problem, hope it's helpful.

---

### Post by mills on 2007-04-20
shouldnt the restricted drivers manager see wether you have them installed?

ps iam writing from windows xp cuz the freezes are just too frequent to make a post

i

---

### Post by kinson on 2007-04-21
My desktop kept crashing an hour ago too. For me it was caused by GAIM(I'm not sure why).

When it logged it, it kept complaining that my msn contact XXX was not on the server list(or something like that), and I'm assuming there's a pop up for every contact of mine behind that pop up....And it's just be super slow, or crash my desktop until my mouse/keyboard doesn't respond either. CTRL+ALT+BACKSPACE doesn't work either.

So I'm currently not running GAIM, and I'll need to sort this out soon. Could this be your problem perhaps?

My advise would be to disable auto startup(if you have enabled it) for those programs (e.g. GAIM, Firefox, Thunderbird), and try and isolate the problem. If the desktop crashes when you're not running GAIM, then its probably not GAIM...etc etc. Then when you've managed to determine which app is causing the freeze, we can work from there :)

Good luck..I hate it when the desktop freezes :(

Cheers,
Kinson

---

### Post by FuturePilot on 2007-04-21
My laptop used to do that. The culprit ended up being the compositing such as Beryl or Compiz or even xcompmanager. That's why I've given up trying to get Beryl to work properly on my laptop. Lower end graphic cards seem to have trouble with compositing. What kind of card do you have? Try running Feisty for a while with the Desktop Effects off.

---

### Post by whitetux on 2007-04-23
I'm constantly getting freezes also. Seems to happen the most when using Firefox and Gaim. Hard power off is the only way to get back to work. Using 6.10, nothing shows up in any of the system logs that looks suspicious and no crash reports. It just boots up as if nothing happened.

Firefox 2.0.0.3
Gaim 1:2.0.0+beta3.1
Linux Restricted Modules 2.6.1 with ATI Mobility Radeon X1600

Hate the freezes!

---

### Post by Elcoco on 2007-04-23
try remaking your xorg.conf with ```
sudo dpkg-reconfigure -phigh xserver-xorg
``` and then ```
sudo nvidia-xconfig --add-argb-glx-visuals --composite
``` to be able to use the desktop effects.

---

