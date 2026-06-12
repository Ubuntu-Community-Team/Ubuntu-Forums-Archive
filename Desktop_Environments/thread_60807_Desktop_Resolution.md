---
title: "Desktop Resolution"
date: 2005-08-29
forum: Desktop Environments
---

### Post by wadesmart on 2005-08-29
08292005 1018 GMT-5

I have a 19in screen with a 1280 by 1024 resolution but it looks giant and the apps take up lots of room compared to the same resolution under my previous Windows XP set up. Is there anything I can do about this? 

There isnt a higher res on the settings. 

Wade

---

### Post by KingBahamut on 2005-08-29
Whats your video card? 

make and Manufacturer of your monitor?

---

### Post by wadesmart on 2005-08-29
08292005 1026 GMT-5

I have a Gateway computer about 1 year old with a Intel Graphics card.

The monitor is a Envision EFT920 19" monitor, specifications here:
[http://www.envisiondisplay.com/products.asp?EPage=products&SMenu=eft920](http://www.envisiondisplay.com/products.asp?EPage=products&SMenu=eft920)

Wade

---

### Post by tag on 2005-08-29
I don't know if there is a technical Problem or if its just the "adjustment phase" but My Impression of the desktop was the same here. I used this Tutorial to fix the "blurred" and way too big fonts [http://convexhull.com/mandrake_fonts.html](http://convexhull.com/mandrake_fonts.html)

That made my desktop much more usable.

---

### Post by KingBahamut on 2005-08-29
Hmmmm....

you can try to edit your xorg.conf file in /etc/X11 to reflect the modes you wish to express, but doing so may or may not cause X to crash. 

    Subsection "Display"
        Depth       24
        #Modes "1440x900" "1024x768" "800x600" "640x480"
        Modes "1024x768" "800x600" "640x480"
        #Modes "1600x1200"
    EndSubsection

EndSection

Set the Modes the resolutions you want. Im assuming that 24 bit depth is your default. 

If you have any questions about this, paste your xorg.conf contents in here and Ill/We'll tell you what to edit and what not to edit.

---

### Post by KingBahamut on 2005-08-29
Tag, your avatar scares me.

---

### Post by wadesmart on 2005-08-29
08292005 1049 GMT-5

Tag, for me its not the fonts but just the physical size of everything. You know when you switch from a lower res to a high res, the stuff on the screen now has more space round it so your applications can be made larger with more room to work. I just feel cramped on the screen right now. 


Thanks King, Ill check that now.

---

### Post by wadesmart on 2005-08-29
08292005 1057 GMT-5

Hey King, 

This is the last entry in the Display:

SubSection "Display"
     Depth      24
     Modes     "1280x1024" "1280x960" "1024x768" "800x600" "640x480"
EndSubSection

And Im already at 1280 x 1024 res. 

So Im assuming that this is just a difference between Windows and Linux. That this display even though its at 1280x1024, its just not as big?

Wade

---

### Post by outtacontrol on 2005-09-07
Once you edit your xorg.conf file, do you need to restart X to display the new screen resolution values?


[QUOTE=KingBahamut]Hmmmm....

you can try to edit your xorg.conf file in /etc/X11 to reflect the modes you wish to express, but doing so may or may not cause X to crash. 

    Subsection "Display"
        Depth       24
        #Modes "1440x900" "1024x768" "800x600" "640x480"
        Modes "1024x768" "800x600" "640x480"
        #Modes "1600x1200"
    EndSubsection

EndSection

Set the Modes the resolutions you want. Im assuming that 24 bit depth is your default. 

If you have any questions about this, paste your xorg.conf contents in here and Ill/We'll tell you what to edit and what not to edit.[/QUOTE]

---

### Post by wadesmart on 2005-09-07
09072005 1418 GMT-5

If you made the change and nothing happened, just restart gnome. 

Press 'Ctrl + Alt + Backspace

Wade

---

