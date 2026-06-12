---
title: "HELLLLPPPP y doesn't my computer like effectts"
date: 2009-04-25
forum: General Help
---

### Post by flyingsliverfin on 2009-04-25
im very annoyed at my computer:

2 weeks ago, the computer had everything: desktop cube, extra effects and so on.

something happened and now it doesn't like effects!!!! when I try to enable then it says: "Desktop effects could not be enabled"


what happened and what can I do?

---

### Post by soro2005 on 2009-04-25
First thing, you should try to remember what you did before it stopped working, and then, you can describe a little better what exactly is the problem. How do you try to reenable the effect? What is the exact text of the error message?

---

### Post by flyingsliverfin on 2009-04-25
im sorry, but I don't have a clue about what i did (although it might have been that I installed/uninstalled something. ive been trying to customize ubuntu for myself more program-wise)

first thing I tried to do to reenable was to go to system-> preferences-> appearence-> visual effects     tried to do "extra" there, but then it gave the message (after restarting gnome.think that becuz the whole screen disappeared then reappeared, but desktop stayed the whole time)

the error message was: Desktop effects could not be enabled

I was wondering if there was a way to enable through the terminal, that should show the different errors in more detail

---

### Post by nikgare on 2009-04-26
You need to make sure that the correct drive is being used for your graphics card.
When you go to **System->Administration->Hardware Drivers** what, if anything does it say about graphics drivers?

Which graphics card do you have? - please post the output of **lspci**

---

### Post by soro2005 on 2009-04-26
If the desktop effects cannot be enabled from the graphical tool, then you won't be able to force them through the terminal either. In most of the cases, the problem is with an inappropriate driver for the gpu (graphics card). If the good one is not installed, then Ubuntu falls back to some subsidiary solution in which you cannot enable the desktop effects. That may be the case in your situation.

Bottomline: Make sure that you have the right driver installed for your graphics card. What is your model, anyway?

You may also want to try to reconfigure Xorg. Log out and open a terminal, or start into failsafe and issue:
```
sudo dpkg-reconfigure xserver-xorg
```
Only do this if you're up for a ride. It should normally not make it worse, but it's definitely not for the faint at heart.

---

### Post by flyingsliverfin on 2009-04-26
thanks for making me check my graphics card driver.
it didn't look like any were enabled. Now I enabled version 180
the drivers 

Ilpci= 01:00.0 VGA compatible controller: nVidia Corporation NV43GL [Quadro FX 540] (rev a2)

let me see if the effects work after my restart 
ill post again then

---

### Post by flyingsliverfin on 2009-04-26
all solved!!!

stupid graphics card driver...

thx every1

---

