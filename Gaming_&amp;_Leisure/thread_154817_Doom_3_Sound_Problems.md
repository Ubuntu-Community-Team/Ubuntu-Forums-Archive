---
title: "Doom 3 Sound Problems"
date: 2006-04-03
forum: Gaming &amp; Leisure
---

### Post by gman646 on 2006-04-03
Hello all, 

I just installed Doom 3 for Linux (on Ubuntu Dapper).

The problem is that alsa sound is all distorted, And OSS doesn't give me any sound. Is there any way to fix alsa distortion?

---

### Post by evilgold on 2006-04-03
[QUOTE=gman646]Hello all, 

I just installed Doom 3 for Linux (on Ubuntu Dapper).

The problem is that alsa sound is all distorted, And OSS doesn't give me any sound. Is there any way to fix alsa distortion?[/QUOTE]

I have the same problem, havnt found a solution yet. what kinda sound card do you have?

---

### Post by gman646 on 2006-04-03
I have a Sound Blaster live, and im using a usb hedset

i think my OSS is the oss sees my hedset as a sound card, i know that oss works when I set programs to use dsp1 and not dsp

---

### Post by evilgold on 2006-04-04
if you get distorted sound (instead of no sound) i dont think its the headset.

I have an onboard c-media chipset, no headset, and it seems i have the same problem as you.

Perhaps it is somthing else with oss. Anyway to use alsa with doom3?

---

### Post by gman646 on 2006-04-04
> if you get distorted sound (instead of no sound) i dont think its the headset.

I have an onboard c-media chipset, no headset, and it seems i have the same problem as you.

Perhaps it is somthing else with oss. Anyway to use alsa with doom3?

You have it backwords OSS dosen't give sound and alsa is distorted. I know ubuntu 5.10 worked fine with doom 3. I would really like to use alsa dose anyone have anyidea how to get this fixed?


And evilgold, try starting doom 3 with this > doom3 +set s_driver oss

if OSS works on your pc that will fix your problem.

---

### Post by Phil_McCrackin on 2006-05-28
Just wondering if anyone has found a solution to this problem yet. Just installed Doom 3 on Dapper. Everything looks GREAT except (like others) distorted sound on best setting and none on oss and alsa. Tried all of the afore mentioned solutions to no avail.

EDIT: Problem Resolved

I actually discovered the solution within Ubuntu forums, however I found it through Google... never stumbled accross it searching internally. At any rate, I closed the window and don't know if I can find it again (just so you know the credit is not mine), but here is the solution:

Open Teminal 
(if you used default path for install...if not just use the path to your doom3)
```
sudo gedit /usr/local/games/doom3/doom3
```

edit the last line to:
```
exec ./doom.x86 "+set s_driver oss"  "+set NumberOfSpeakers 2"
```

open the game if sound is still not working, change sound to oss in options->system and restart game...voila!

---

