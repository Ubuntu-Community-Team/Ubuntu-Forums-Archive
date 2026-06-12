---
title: "Unity 3D stops working after changing Compiz settings"
date: 2011-10-24
forum: Desktop Environments
---

### Post by fraktalek on 2011-10-24
Hi,

my Unity 3D stopped working after I ran Compiz settings ccsm and tried to change OpenGL settings. 

I was experiencing slow/choppy windows dragging so I thought I'd try to change the Sync to VBlank setting. Now I can't see the top and left panels in Unity 3D, Unity 2D works ok. 

ccsm is showing the same settings as before I started changing them.

How do I go back to the original settings? unity --reset does NOT change a thing about the current state.

There's this question already on askubuntu by someone else: [http://askubuntu.com/questions/69814/unity-3d-stops-working-after-changing-compiz-settings](http://askubuntu.com/questions/69814/unity-3d-stops-working-after-changing-compiz-settings) I believe it is wrongly marked as a duplicate because unity --reset does not work.

---

### Post by jalberro on 2011-10-24
I solve several problems with this: 

[http://ubuntuforums.org/showpost.php?p=11386080&postcount=4](http://ubuntuforums.org/showpost.php?p=11386080&postcount=4)

---

### Post by mc4man on 2011-10-24
unity --reset is not working because you are possibly using the "Default" profile instead of the "unity" profile in ccsm

If you want to keep using the "Default" profile then log into _ubuntu_ > Ctrl+Alt+T, in the terminal go ccsm & enable the Unity plugin

Otherwise try this - 
Log in to the ubuntu session, open a terminal & go 
```
nautilus ~/.config/compiz-1/compizconfig
```
The will be a file named config there
Open it up & delete all the contents, save.
Then log out using Ctrl+Alt+Delete

If when you log back into the ubuntu session all is not well then again open a terminal & use unity --reset

---

### Post by Frogs Hair on 2011-10-24
This has worked for some users .```
gconftool-2 --recursive-unset /apps/compiz-1
unity --reset
```

---

### Post by fraktalek on 2011-10-24
Thanks all for the fast answers!

Enabling the Unity plugin in ccsm solved my problem with the panels, great :)

---

### Post by mc4man on 2011-10-24
> **fraktalek said:**
> Thanks all for the fast answers!

Enabling the Unity plugin in ccsm solved my problem with the panels, great :)
I'm not sure if there is any downside to using the Default profile vs the unity profile.
If it seems a bit different then empty that file I mentioned & do a log out/in

---

### Post by rcstook on 2011-10-24
> **fraktalek said:**
> Thanks all for the fast answers!
 
Enabling the Unity plugin in ccsm solved my problem with the panels, great :)
 
 
I'm  new... and having a similar problem.
Can you show exactly how you 'enabled unity plugin' so I can try it.
 
Thanks.

---

### Post by fraktalek on 2011-10-24
> **rcstook said:**
> I'm  new... and having a similar problem.
Can you show exactly how you 'enabled unity plugin' so I can try it.
 
Thanks.

First you have to run CompizConfig Settings Manager. You do it for example by running ccsm from the terminal (press Ctrl+Alt+T to open a new terminal), alternatively from Dash (the left-hand panel that you may or may not see now), or maybe Alt+F2.

In ccsm type "unity" to the Filter search field in the top-left side of the window. It will find the "Ubuntu Unity Plugin" in the Desktop category. Just make sure that it is checked.

Then unity --reset should work

---

### Post by rcstook on 2011-10-24
That got my desktop back. Thanks!
But the 'unity --reset' command didn't run smoothly.
Seemed several things couldn't be found or initialized.
Seems now if I open a window (firefox) it opens full screen.
If I try to minimize that window, I then lose the task bar options to close, minimize, or expand. The menu bar for 'file, edit, ect...' is the only thing that appears.
 
Is there a way to load defaults into the ccsm or unity default settings?
 
Maybe uninstall ccsm?
 
Thanks again for this help!

---

### Post by fraktalek on 2011-10-24
you would have to be more specific about the errors that you see after your unity --reset

the fact that you don't see the min/max/etc buttons probably means that unity did not actually start, or better said it's window manager compiz.. I don't know much about the details.

Anyway, you can load default settings in ccsm in the Preferences section (lower left button), then there's the button "Reset to defaults" in the "Profile & Backend" tab.

---

### Post by rcstook on 2011-10-24
OK.
Thanks again.
 
I have been looking around and seems compiz is not stable with 11.10.
 
I've got some things to try after looking around the forum.
 
I'll be back if I continue to have problems.

---

### Post by Jayyin11043 on 2011-10-24
anyone know how to fix unity opening the windows (programs) above my window so that the close program and stuff are outside my desktop, I've tried using centre windows but that makes it so that windows cannot be moved. 

I upgraded from 11.04 to 11.10

---

