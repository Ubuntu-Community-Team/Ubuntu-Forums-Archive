---
title: "Loading CompizFusion at startup"
date: 2007-06-26
forum: Desktop Effects &amp; Customization
---

### Post by Matuku on 2007-06-26
I have read many threads about people with problems about this saying something about adding it to the sessions but I cannot work out how to do this for myself; firstly how do I get to the sessions options and secondly which part do I have to add the option to and thirdly what do I need to add? Is it: ```
compiz --replace cpp
```
Quite detailed instructions would be appreciated; I am a self-admitted noob (but I got compizfusion working so thats a start).

Thanks

---

### Post by AriciU on 2007-06-26
System / Preferences / Sessions / New / Name: "Compiz" / Command: "compiz --replace -c emerald &"

---

### Post by Matuku on 2007-06-27
> **AriciU said:**
> System / Preferences / Sessions / New / Name: "Compiz" / Command: "compiz --replace -c emerald &"
That doesn't seem to have worked; now it starts up as normal and the Ubuntu loading bar (which has Nautilus as being loaded last it seems on mine) appears and then disappears, but as soon as I click on anything it reappears again and I cannot do anything until I have used alt+F2 to enter "compiz --replace cpp". During the time before I enter that any windows I start up have no borders.

EDIT: A thought came into my head whilst I was typing the above but I had to test it first; it does load on startup but only kicks in 2-3 minutes after everything else. Is there anyway to show how it is progressing etc, so I can tell when it is ready?

---

### Post by AriciU on 2007-06-27
Leave that line alone in sessions.

Open up gconf-editor and go to desktop/gnome/applications/window_manager

Set "current" and "default" to /usr/bin/metacity

Reload gdm / restart and compiz should load fine now.

If you're not getting any windows borders then go to System / Administration / Synaptic packet manager and search for "libdecoration". You will find 2 entries, libdecoration and libdecoration-dev. Mark them both for upgrade/install and click apply.

Also, make sure that you have the line 

> Option         "AddARGBGLXVisuals" "true"

in /etc/X11/xorg.conf under the "Screen" section.

Also add this line to the end of your xorg.conf

> Section "Extensions"
    Option "Composite" "Enable"
EndSection

---

### Post by shinjo101788 on 2007-06-27
i have the same problem. i did waht you said and now i cant get into my xserver lol . it says no screens found. is there a way to edit the file in the command line.  i think the 3 lines i added a at the end screwed it up.

---

### Post by kpolice on 2007-06-27
Comment out the lines with a # .

Also remember to always backup your files, specially if they are system files.

---

### Post by shinjo101788 on 2007-06-27
i dont know the command to edit it. :)

any ideas.

---

### Post by Matuku on 2007-06-27
How do I get gconf-editor up?

---

### Post by AriciU on 2007-06-27
Type gconf-editor in the console.

shinjo: pico /etc/X11/xorg.conf and put a # in front of the lines you added. Those lines are for nvidia btw... don't know if you have an ATI card and they screw it up.

---

### Post by shinjo101788 on 2007-06-27
i have a geForc7900 gtx go

---

### Post by shinjo101788 on 2007-06-27
> **Matuku said:**
> That doesn't seem to have worked; now it starts up as normal and the Ubuntu loading bar (which has Nautilus as being loaded last it seems on mine) appears and then disappears, but as soon as I click on anything it reappears again and I cannot do anything until I have used alt+F2 to enter "compiz --replace cpp". During the time before I enter that any windows I start up have no borders.

EDIT: A thought came into my head whilst I was typing the above but I had to test it first; it does load on startup but only kicks in 2-3 minutes after everything else. Is there anyway to show how it is progressing etc, so I can tell when it is ready?

THANK YOU!!!!!!!!!! IT WORKS

---

### Post by Matuku on 2007-06-27
> **AriciU said:**
> Leave that line alone in sessions.

Open up gconf-editor and go to desktop/gnome/applications/window_manager

Set "current" and "default" to /usr/bin/metacity

Reload gdm / restart and compiz should load fine now.

If you're not getting any windows borders then go to System / Administration / Synaptic packet manager and search for "libdecoration". You will find 2 entries, libdecoration and libdecoration-dev. Mark them both for upgrade/install and click apply.

Also, make sure that you have the line 



in /etc/X11/xorg.conf under the "Screen" section.

Also add this line to the end of your xorg.conf

Can you explain what this all does (just for my knowledge)? Well my knowledge and that it worked and now isn't.

---

### Post by AriciU on 2007-06-27
It loads the standard metacity window manager at startup (become it starts very fast, unlike compiz) then starts compiz instantly.

---

### Post by keesjelol on 2007-06-27
> **AriciU said:**
> Leave that line alone in sessions.

Open up gconf-editor and go to desktop/gnome/applications/window_manager

Set "current" and "default" to /usr/bin/metacity

Reload gdm / restart and compiz should load fine now.

If you're not getting any windows borders then go to System / Administration / Synaptic packet manager and search for "libdecoration". You will find 2 entries, libdecoration and libdecoration-dev. Mark them both for upgrade/install and click apply.

Also, make sure that you have the line 



in /etc/X11/xorg.conf under the "Screen" section.

Also add this line to the end of your xorg.conf


you said no window borders, thats my problem, i found those two entries , didn't work.

to explain my problem clearer i alt+f2 and select "compiz --replace" and the borders disappear, but if i go back to metacy i get the borders back. I would really like borders in compiz other wise i can't move the windows :(

any advice?

---

### Post by AriciU on 2007-06-27
Compiz fusion or regular compiz witch you select thru beryl-manager? I'm running fusion and it did the trick for me. Don't know what else you can do about it.

---

