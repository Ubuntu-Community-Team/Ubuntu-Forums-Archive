---
title: "Compiz Ubuntu 7.10 locking mouse to cube?"
date: 2007-10-24
forum: Desktop Environments
---

### Post by tongata on 2007-10-24
ok heres my question in beryl you could hit Ctrl+Alt to lock mouse to cube and rotate it manually without holding any buttons.
How do I do this with Compiz???




Thanks

---

### Post by fatespeaks on 2007-11-25
Any answers for this?  I would like Compiz to stay in rotate-cube mode without holding buttons.  This will allow me to demonstrate the effect and take photos.  I had hoped to find an action in CompizConfig to bind a key for this function.
-Aaron

---

### Post by Rowdy73 on 2007-11-25
System>  

preferences> 
 
advanced desktop effects settings>

rotate cube> 

actions> 

general drop down tab>

initiate>

Doing this will allow you to assign a key on your keyboard to holding the cube screen open and allow you to rotate the cube with your mouse. Hit Esc to turn off the effect.

---

### Post by JECHO on 2007-11-25
> **fatespeaks said:**
> Any answers for this?  I would like Compiz to stay in rotate-cube mode without holding buttons.  This will allow me to demonstrate the effect and take photos.  I had hoped to find an action in CompizConfig to bind a key for this function.
-Aaron



im not sure if this answers your question but it sounds like you just dont want to use keys on the keyboard to activate the cube... if thats so, you can also just click both the right and left mouse buttons on the desktop (and hold them) then use the mouse to spin the cube. this way your other hand is free to take a screenshot or whatever of the desktop.

---

### Post by Rowdy73 on 2007-11-25
> **JECHO said:**
> im not sure if this answers your question but it sounds like you just dont want to use keys on the keyboard to activate the cube... if thats so, you can also just click both the right and left mouse buttons on the desktop (and hold them) then use the mouse to spin the cube. this way your other hand is free to take a screenshot or whatever of the desktop.

That will work, but the way i suggested will not require you to hold ANY button or key.

---

### Post by Matteus_Blanc on 2008-01-31
Hi,
This is a really good question and when you get this working it makes compiz even better. It's strange there doesn't seem to be too much info on how to do it out there.

OK let me start this by saying that I am an openSuSE user running KDE. I have never used Ubuntu but since Compiz and KDE are common to both SuSE and Ubuntu, it shouldn't matter.

So to get the cube to show without pressing any keys do the following (for KDE):
1. you need to install the compiz fusion icon (to all you to access the CCSM)
2. install the KDE backend - I have this: libcompizconfig-backend-kconfig 0.7.2-2.12- kconfig backend for  Compizconfig-settings-manager(ccsm)
3. you may need to restart the machine here, or at least the Xserver (ctrl+alt+del) or compiz
4. next go to the CCSM (do this by right clicking the fusion icon) and select  PREFERENCES (right hand side near the bottom). Set the backend to KDE
5. You should now find that when you hit the middle mouse button the cube is shown. A left click will pull the closest face into frame.
6. If you have followed steps 1 through 5 without success try another restart of the graphics system

This feature is really good, not least because you can leave the cube skewed, with a nice skydome, for all the windows users to admire as they walk past your machine.

There is a gnome version of the back-end too. Can't say how well that one works though...

Hope this one helps somebody out.

Matteus

---

### Post by fatespeaks on 2008-02-29
Rowdy73:  Thank you.  That worked, but only without modifier keys.  For example, <Ctrl><Alt>r will initiate, but snap back when I release a key.  However, r will initiate and stay in rotate mode.  And I would not suggest using a letter key because it will initiate regardless of which app has the focus.  BTW, how do I switch back to Disabled?

Cheers,
Aaron

---

### Post by Rowdy73 on 2008-02-29
> **fatespeaks said:**
> Rowdy73:  Thank you.  That worked, but only without modifier keys.  For example, <Ctrl><Alt>r will initiate, but snap back when I release a key.  However, r will initiate and stay in rotate mode.  And I would not suggest using a letter key because it will initiate regardless of which app has the focus.  BTW, how do I switch back to Disabled?

Cheers,
Aaron

System>

preferences>

advanced desktop effects settings>

And just uncheck the box that applies to the action you need to have stop working.

Esc also works to get the cube stop working in my case, (temporarily).

---

