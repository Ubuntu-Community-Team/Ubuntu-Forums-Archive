---
title: "Ouch! Suddenly only black desktop when logging in!"
date: 2008-07-28
forum: Desktop Environments
---

### Post by DizMan on 2008-07-28
Hi there!

I'm very green when it comes to Kubuntu or Linux in general.

Here's my problem. I installed Kubuntu 8.04 with KDE 4,0. It all looked nice, and I managed to boot it at couple of times, fetch updates and configure various apps.

But suddenly when i log in, the desktop (screen) is just black. There are no icons or buttons or anything. I don't have a clou, why this happened. I may have pressed some keys by accident but I do not remember to have messed with desktop or video settings. So now I can't use Kubuntu and have to turn the machine off by using the power button.

Please help here - else I'm stuck with Win Vista! Looking forward to hearing from you!

Greetings from
Diz


specs: HP Pavilion DV9780eo, Intel core 2 Duo T7500, 3 gigs RAM, Nvidia GeForce 8600M GS, 2x250 gigs HD, dual boot Kubuntu 8.04 and Windows Vista Premium

---

### Post by kuja on 2008-07-28
Start in "recovery mode", if it asks you'll want a root shell. From there, try running this command (substituting as necessary)

```
mv /home/yourusername/.kde4 /home/yourusername/.kde4.backup; exit
``` and have it start up as usual and see if you still get the black screen.

---

### Post by sandeepy on 2008-07-28
It would also help if you remove other hidden directories in your home such .ICE* and a few more. Just check which of these get updated everytime you login. Best soln would be to delete (before backing them up) all hidden directories once and then try logging in again.

---

