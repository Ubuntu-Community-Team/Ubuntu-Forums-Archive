---
title: "Ubuntu and Compiz? What happened?"
date: 2009-01-30
forum: General Help
---

### Post by Bunez on 2009-01-30
Okay Im a newb and I just started using Ubuntu 8.10 this month. Today I screwed around the graphics settings (some stuff in compiz, I think changed the texture filter to best and i set the refresh rate way high (stupid I know). 

Anyways, I was also updating and when I restarted everything went haywire. The screen had funny lines through it and the desktop was like split in half. A prompt came saying that my graphics drivers could not be properly detected. It gave me a few options and I picked "return to default settings". After I did that and restarted, things were okay again. THe only problem is I cannot turn on my compiz effects and I can't seem to install any packages. 

Every time I try to install a package it says it wants me to do "Dpkg --a" or something. I tried that in terminal but it said it wasnt a valid command. Could someone please help me?

---

### Post by Sealbhach on 2009-01-30
Can you copy and paste here the message you get when you try to install something?

How are you attempting to turn on the Compiz effects? Is it in the Appearance Manager? Ticking the Extra box? If your graphics driver is not enabled that would stop you doing that. Look in System/Administration/Hardware Drivers and see if your driver is enabled.


.

---

### Post by jmszr on 2009-01-30
Bunez,
         Try:```
sudo dpkg --configure -a
``` and see what that does. Also what Sealbhach says.

---

