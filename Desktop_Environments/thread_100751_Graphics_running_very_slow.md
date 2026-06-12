---
title: "Graphics running very slow ?"
date: 2005-12-08
forum: Desktop Environments
---

### Post by scruffy on 2005-12-08
Hello all :D

I have fired up ubuntu on two of my machines, one has an nvidia 6600 and the other a Radeon 9800 pro. When the screensavers come on they run extremely slowly as if there is no hardware acceleration at all, is there something I should do a setting or something. I have read the forums and done a few searchs but just became confused ( sorry only day three on linux for me, complete beginner ).

Hopefully one of you brighter souls will know the answers.

Regards

Scruffy

---

### Post by scruffy on 2005-12-08
Well im still struggling on this one. I have reinstalled ubuntu 5.10 breezy. Everything goes great, it finds all my hardware, and works great. It updates itself fine, yet I still am struggling with getting any kind of decent graphics, even the application windows and  sceensavers run slowly?

Can anyone shed any light on whats going wrong? I get the same thing in both x32 and x64 versions, so at the moment gameplay will definatley be out of the question.

Thanks in advance 

Scruffy

---

### Post by fordfan753 on 2005-12-08
You need to install the proper graphics drivers for your cards. Search for HOWTOs on the forums about doing this, because there should be heaps. For a nVidia card I would normally:

```
sudo apt-get install nvidia-glx nvidia-kernel-common nvidia-settings
sudo nvidia-glx-config enable
```

You may or may not need the restricted modules for your kernel, I don't remember. If any of these things aren't found by apt-get, make sure you have the universe repository.

For the ATI card I have no idea, someone around here would...ie: someone please post :P

Oh, and also use ```
glxgears --iacknowledgethatthistoolisnotabenchmark
``` before and after you install the drivers, if the install worked you should see a big difference in the frame rates ;)

---

### Post by scruffy on 2005-12-08
Fantastic :D

Thanks for the reply fordfan, I'll give it a try when I get back from work, and let you know how I get on.


Thanks again 

Scruffy

---

### Post by RAOF on 2005-12-08
A better diagnostic of OpenGL accelleration is actually "glxinfo".  It gives you all sorts of information about your OpenGL system.  The important bits which show that 3d accelleration is working are:
"direct rendering: yes" and
"OpenGL vendor string: " being something **not** "MESA" - the MESA libraries are a software OpenGL implementation.

---

### Post by fordfan753 on 2005-12-08
[QUOTE=RAOF]A better diagnostic of OpenGL accelleration is actually "glxinfo".  It gives you all sorts of information about your OpenGL system.  The important bits which show that 3d accelleration is working are:
"direct rendering: yes" and
"OpenGL vendor string: " being something **not** "MESA" - the MESA libraries are a software OpenGL implementation.[/QUOTE]

I would use glxinfo myself, but when I set nVidia drivers up for my friends I always like them to see 20-30 frames before, and 3000 after, just to show them how much of a difference it makes.

---

### Post by RAOF on 2005-12-08
[QUOTE=fordfan753]I would use glxinfo myself, but when I set nVidia drivers up for my friends I always like them to see 20-30 frames before, and 3000 after, just to show them how much of a difference it makes.[/QUOTE]
Even after typing in the option --iacknowledgethatthistoolisnotabenchmark? :p

---

### Post by scruffy on 2005-12-08
Is it the same for installing nforce4 drivers for the motherboard aswell?

Out of interest what sort of fps are you gents getting in games?

---

### Post by scruffy on 2005-12-09
[QUOTE=fordfan753]
```
sudo apt-get install nvidia-glx nvidia-kernel-common nvidia-settings
sudo nvidia-glx-config enable
```
[/QUOTE]


Worked like a charm thanks fordfan=D> 

Screensaver (the ants in the balls one ) fps went from 20-40 before your advice to 600-700 + in full screen mode, so a happier bunny here now. Thanks.

Does anyone know a simple way of installing nvidias nforce4 motherboard drivers aswell.

All the best

Scruff

---

### Post by RAOF on 2005-12-11
You probably don't need the motherboard drivers.  Is there any functionality that you need from it that you don't have?  Is the onboard sound working?  The onboard networking?  If the answer is "yes" to both of these (or "I don't know because I don't use them") then you don't need the mb drivers.

---

### Post by okt on 2005-12-11
I too am having really slow graphics, I however am running an ATI card.

I tried to get fglrx to work but when changing the xorg.conf under devices to use fglrx instead of ati, when I restart X it blows up at me and refuses to load properly.

---

