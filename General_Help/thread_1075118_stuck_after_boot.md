---
title: "stuck after boot"
date: 2009-02-19
forum: General Help
---

### Post by mikedmor on 2009-02-19
I was working with wine (only fonts to repair some problems i was having) when all of a sudden nothing would open anymore. well i thought ok i probably just need to restart. well as soon as i rebooted and got back to where the login screen was suppose to boot i get stuck in the brownish screen with my mouse showing that is is loading. 

ALT+F2,F3,F4,ETC does not work either. but i can boot into the recovery mode but idk how to repair. Do i have to remove wine? that would really be upsetting...

Does anybody have a solution PLEASE!!!

-mike

---

### Post by overdrank on 2009-02-19
> **mikedmor said:**
> I was working with wine (only fonts to repair some problems i was having) when all of a sudden nothing would open anymore. well i thought ok i probably just need to restart. well as soon as i rebooted and got back to where the login screen was suppose to boot i get stuck in the brownish screen with my mouse showing that is is loading. 

ALT+F2,F3,F4,ETC does not work either. but i can boot into the recovery mode but idk how to repair. Do i have to remove wine? that would really be upsetting...

Does anybody have a solution PLEASE!!!

-mike

Hi and you may try and boot into recovery mode and you will be given 4 option and I believe the last is xfix. After selecting it and completing you should be give the 4 options again and choose to boot normally.

---

### Post by mikedmor on 2009-02-19
no still nothing. the screen did flicker this time though. but its still just showing only the loading circle cursor...

---

### Post by overdrank on 2009-02-20
> **mikedmor said:**
> no still nothing. the screen did flicker this time though. but its still just showing only the loading circle cursor...

Ok what is the model of the graphics card and version of Ubuntu you are using?
If you cant use the ctrl, alt, F1 keys to reach the command line at the login window then boot into recovery mode. Then choose command prompt and 
use the commands 
```
sudo /etc/init.d/gdm stop

Then
sudo dpkg-reconfigure -phigh xserver-xorg

Then 
sudo /etc/init.d/gdm start

```
Hopefully this will get you back to the desktop

---

### Post by mikedmor on 2009-02-20
nope... still the problem. and im using a NVIDIA GeForce 9600 GT.

idk why this is doing this, could it be cause of me messing with the fonts?

Ugh and i though i had just got my pc to finally. i have been having problems with it for the past two weeks. just solved those and now this. :-P

EDIT: BTW ALT+F1 took me back to the recovery mode root shell prompt.

---

### Post by mikedmor on 2009-02-20
anyone? I really need my pc working by tonight. im going to a friends house. 

Please help!

---

### Post by mikedmor on 2009-02-20
well without much help i found out a way to get some more information. i stopped the GDM as you said. but this time used startx and it logged me in, mouse not working though, but if i click ALT+F1 here is the output:

(==) Log file: "/var/log/Xorg.0.log", Time: Fri Feb 20 19:27:19 2009
(==) Using config file: "/etc/X11/xorg.conf"
(EE) Failed to initialize GLX extension (Compatible NVIDIA X driver not found)


Thats all it says... maybe a step closer... Any help?

---

### Post by mikedmor on 2009-02-20
ok got the mouse working. but no top and bottom menu. so it has to do with the xserver not starting right. cause now im logged in. i got the login sound even. and my background loaded. so how do i fix the xserver? correctly?

---

