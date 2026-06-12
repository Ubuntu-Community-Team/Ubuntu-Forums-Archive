---
title: "Wow installation problems!"
date: 2007-02-03
forum: Gaming &amp; Leisure
---

### Post by Bofur on 2007-02-03
I've tried almost everything but wow will not install. I copied the files to my desktop(also tried w/ cds too) I direct cedega to the install file. It loads for a second then a white box in the corner pops up. In terminal I get the message
"wine: Unhandled exception, starting debugger...". I have the latest nvidia drivers, and I'm using Ubuntu 6.10. If anyone could please help me I'd appreciate it!!!

Also.. please dont recommend wine to me, I'm not paying 5 dollars a month to use a different program.

---

### Post by glabouni on 2007-02-03
as a paying customer, you should try to get support from cedega.

I know it's not really helping but I don't play wow (I see no point in this game except making blizzard richer and people addicted), and all I could say to help is that I've a friend who has it working with wine.

---

### Post by Sammi on 2007-02-03
I'm playing WoW in Wine as we speak with good framerates.

This guide lists in all three different ways of getting WoW installed on Ubuntu: [https://help.ubuntu.com/community/WorldofWarcraft](https://help.ubuntu.com/community/WorldofWarcraft)

Have you tried them all?

---

### Post by Bofur on 2007-02-03
I guess I'll have to, since cedega wont work. Thanks for the guide!

---

### Post by Jarn on 2007-02-03
I think you are using Wine. Based on the fact you said you didn't want to use Wine because it "costs $5 dollars a month" and that the error message you gave said "wine". *Cedega* is the one that costs $5 a month whereas Wine is free.

---

### Post by Bofur on 2007-02-03
Ok.

---

### Post by Sammi on 2007-02-03
If you are having problems, then please make sure you have tried out all of the tips found in the troubleshooting section of the howto, before posting back.

If the tips in the guide didn't help you then please post the output of these commands:    [LEFT]```
glxinfo | grep vendor [LEFT]glxinfo | grep 'OpenGL version'[/LEFT]
 
```[/LEFT]
 
  And let this command run for a while, say 30 seconds, then post the output: [LEFT]```
glxgears -printfps
```[/LEFT]
 
Also try comparing how the game runs in -opengl and -d3d mode.

---

### Post by Bofur on 2007-02-03
```
justin@justin-xt41fi7:~$ glxinfo | grep vendor
server glx vendor string: NVIDIA Corporation
client glx vendor string: NVIDIA Corporation
OpenGL vendor string: NVIDIA Corporation
justin@justin-xt41fi7:~$ glxinfo | grep 'OpenGL version'
OpenGL version string: 2.0.2 NVIDIA 87.76
justin@justin-xt41fi7:~$ glxgears -printfps
86659 frames in 5.0 seconds = 17330.531 FPS
86705 frames in 5.0 seconds = 17340.943 FPS
86662 frames in 5.0 seconds = 17332.268 FPS
86624 frames in 5.0 seconds = 17324.777 FPS
86712 frames in 5.0 seconds = 17342.334 FPS
86704 frames in 5.0 seconds = 17340.762 FPS
86715 frames in 5.0 seconds = 17342.881 FPS
86732 frames in 5.0 seconds = 17346.229 FPS
85605 frames in 5.0 seconds = 17120.955 FPS

```

---

### Post by Sammi on 2007-02-03
You've got a Nvidia card, and you're using the stable driver, which seems to be working fine.

If you are still experiencing problems, then you could consider upgrading to the beta driver. _Please only do this as a last resort_. There are no guarantees with it, but it seems to work well for many people. I have personally had good experiences with using the Envy script from Alberto Milone(ubuntuforums user "tseliot"), for upgrading to it, but please don't scream at me if it doesn't work for you.

Alberto Milone's instructions for bleeding edge Nvidia drivers can be found here:
[Thttp://albertomilone.com/instructions.html](Thttp://albertomilone.com/instructions.html)

The Envy script can be found here:
[http://albertomilone.com/ubuntu/nvidia/scripts/envy_0.8.1-0ubuntu3_all.deb](http://albertomilone.com/ubuntu/nvidia/scripts/envy_0.8.1-0ubuntu3_all.deb)

To run it you must log out, then press CTRL-ALT-F6, log in to the command prompt, and then write "envy" and press enter.

---

