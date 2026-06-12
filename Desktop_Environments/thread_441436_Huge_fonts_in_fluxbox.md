---
title: "Huge fonts in fluxbox"
date: 2007-05-12
forum: Desktop Environments
---

### Post by AlexTheMad on 2007-05-12
Hi guys! I've installed fluxbox and I'm really digging this, but there's one problem. The fonts are enormous in everything non-flux related! 

[http://folk.ntnu.no/alexanbj/Screenshot.png](http://folk.ntnu.no/alexanbj/Screenshot.png)

I've been trying to fix this for the last half hour without any luck. Anyone care to help?

Running Feisty, installed flux through aptitude

---

### Post by kerry_s on 2007-05-12
Check your dpi. also if you want to keep your current dpi you can use a gtkrc-2.0 with> gtk-font-name="fontname 10" < replace fontname withe the name of your font and make the size what you want, i usually start at 10.

---

### Post by AlexTheMad on 2007-05-12
okay. that was a little bit too advanced for me :p

edit spelling:

---

### Post by kerry_s on 2007-05-12
Okay, lets try again, were going to use the gtkrc-2.0, that's what i use in my flubox setup. I don't know what editor you have, but i'm guessing you installed fluxbox on gnome so i'm going to use gedit, replace gedit if it is not your editor.

gedit ~/.gtkrc-2.0
copy and paste this->

gtk-font-name="Sans 10"

save and close

logout and back in to see if it worked.

---

### Post by AlexTheMad on 2007-05-12
Sadly it didn't work. Was the file supposed to exist beforehand? Cause I had to create it. I do have a gtkrc-1.2-gnome2 though. but that file says I'm not allowed to edit it :)

---

### Post by kerry_s on 2007-05-12
It could be the "Sans" i didn't know what font to put, i use verdana in my setup, looks like this-> gtk-font-name="verdana 10"
Try with a different font maybe> "dejavu-sans 10"

Yes you create it if it's not there.

---

### Post by AlexTheMad on 2007-05-13
hey that worked wonders. Verdana 7 was the way to go!! Thank you

---

### Post by kerry_s on 2007-05-13
> **AlexTheMad said:**
> hey that worked wonders. Verdana 7 was the way to go!! Thank you

That's good, i didn't know you had verdana installed.

---

### Post by AlexTheMad on 2007-05-13
Damnit. That turned out to just be a very poor workaround. For **everything** to look normal in flux, I have to run gnome-settings-daemon. What's up with that?

---

### Post by kerry_s on 2007-05-13
All fonts in fluxbox can be set differently, there's no blanket setup like with gnome-settings-daemon. Use gnome-settings-daemon since you have it. Fluxbox takes time to learn how to setup to your liking. Just spend some spare time reading up on fluxbox when you have time, it's very easy but you have to know about the options to do anything with it.

---

### Post by AlexTheMad on 2007-05-13
Okay. I will. Thanks kerry, you've been really helpful. One last question though, if I want flux with IMLIB2 support, I have to compile it myself, and not use the package from the repos?

---

### Post by RedSquirrel on 2007-05-13
I think you will have to compile your own for imlib2.

Check with:

```
fluxbox -i
```

It will probably indicate "-IMLIB2" meaning that it wasn't compiled into the version from the repositories.

And it isn't one of the defaults in the configure script, so you have to enable it:

```
./configure --enable-imlib2

```

---

### Post by HP-X on 2007-09-03
Ok, I know bumping is ugly but I thought I should post this solution here since I didn't find it on the ubuntu forums.

I had the same problem, fonts were ok in gnome & gdm but in fluxbox they became very big and everything became ugly.

This probably only applies to nvidia cards but here's what I did.

Under the Device-part for my nvidia I added Option "UseEDID" "False" which solved everything. Only change in the other apps was that GDM got a smaller font, something that can probably be fixed with updating the gdm theme.

My xorg.conf device section.
```
Section "Device"
        Identifier      "nVidia Corporation NV18 [GeForce4 MX 440 AGP 8x]"
        Driver          "nvidia"
        Busid           "PCI:2:0:0"
        Option          "AddARGBVisuals"        "True"
        Option          "AddARGBGLXVisuals"     "True"
        Option          "NoLogo"        "True"
        Option          "UseEDID"               "False"
EndSection
```

I hope that helps for some people with the same problem as me. =)

---

