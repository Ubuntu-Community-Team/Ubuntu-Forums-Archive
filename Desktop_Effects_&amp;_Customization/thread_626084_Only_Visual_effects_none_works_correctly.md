---
title: "Only Visual effects none works correctly"
date: 2007-11-28
forum: Desktop Effects &amp; Customization
---

### Post by Steve.Chevalier on 2007-11-28
I recently discovered the setting for my monitor (ViewSonic 23") and turned that monitor on.
Ever since I did that the only visual effects "none" works they way it used to.

Any other visual effect settings causes these problems;
Not able to move windows except using the alt key.
No "X" in the upper right corner to close the window.
Terminal opens completely blank

I've tried a reinstall of combiz but that didn't help

I am using release 7.10

Any suggestions?

---

### Post by gsiliceo on 2007-11-28
> I recently discovered the setting for my monitor (ViewSonic 23") and turned that monitor on.
Where did you discovered that setting, what do you mean

---

### Post by Steve.Chevalier on 2007-11-28
I went into System -> Administrations -> Screens and Displays and looked around for the ViewSonic monitor.  I found it in the list and activated it.  Also set it to wide screen.  It looks great but all the other stuff stopped working.  I undid this change, rebooted but all the other problems persisted.

Forgot to mention that I also can not resize any windows in any of the other effects modes.

---

### Post by gsiliceo on 2007-11-28
OK, what graphic card do you have?
And in terminal do this please
> glxgears

---

### Post by Steve.Chevalier on 2007-11-28
NVIDIA GeForce 6800

6313 frames in 5.0 seconds = 1262.506 FPS
6431 frames in 5.0 seconds = 1286.082 FPS
6052 frames in 5.0 seconds = 1210.228 FPS
6615 frames in 5.0 seconds = 1322.999 FPS
8693 frames in 5.0 seconds = 1738.513 FPS
7230 frames in 5.0 seconds = 1445.965 FPS

---

### Post by gsiliceo on 2007-11-28
Ok, this command will add a line in your xorg.conf file that is needed to run compiz in nvidia cards
> sudo nvidia-xconfig --add-argb-glx-visuals -d 24 
Maybe is that what you need

---

### Post by Steve.Chevalier on 2007-11-28
Well, that did the trick.

Just how does one learn these wonderful things???

Thanks you!!

---

### Post by gsiliceo on 2007-11-28
I have the ubuntu forums extension for firefox and i click the unaswered posts every once in a while and i open the posts that most likely are things that i already fixed or stumbled upon to.

=)

---

### Post by nisarg on 2008-03-29
Hello,

I am facing a similar issue and cant seem to find a solution to the problem.
When i switch visual effects ON (i.e to Normal Extra or Custom)  firefox or any other program maximized, the title bar seems empty. i.e I dont see the minimize maximize close controls or the menu. They are there as I can point the cursor and click them and they work, I just cant see them.
When I switch the visual effects to NONE I see everything fine.Only visual effects on NONE works correctly,

Sys info
Graphic card - ATI Radeon - Not sure which model. Can you instruct how to get this, i can get that if needed
Ubuntu 7.10 
Emerald

Cheers

---

### Post by gsiliceo on 2008-03-31
Im sorry, i dont have an ATI card, i don't know what to do.

---

