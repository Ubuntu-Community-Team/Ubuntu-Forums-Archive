---
title: "How to adjust fonts/colors for Putty under Ubuntu"
date: 2011-02-22
forum: Desktop Environments
---

### Post by wonfineday on 2011-02-22
I  just installed Ubuntu and am happy with the color/themes/fonts etc. but  my PuTTY has got really tiny fonts. How can I make them bigger?

TIA.

---

### Post by anglican on 2011-02-23
> **wonfineday said:**
> I  just installed Ubuntu and am happy with the color/themes/fonts etc. but  my PuTTY has got really tiny fonts. How can I make them bigger?

TIA.When you run putty there are various configuration settings in a box on the right hand side of the window. One is Fonts and another Colours. Choose values that you like - I use "Monospace 12" for my ordinary characters. Then choose Session and put in a name in the "Saved Sessions" box and save it so you can load these values next time you run putty. You could also set colors and fonts on the command line or load a session when you run putty (see "man putty").

H

---

### Post by wonfineday on 2011-02-28
> **anglican said:**
> When you run putty there are various configuration settings in a box on the right hand side of the window. One is Fonts and another Colours. Choose values that you like - I use "Monospace 12" for my ordinary characters. Then choose Session and put in a name in the "Saved Sessions" box and save it so you can load these values next time you run putty. You could also set colors and fonts on the command line or load a session when you run putty (see "man putty").

H


I tried that approach but I need to do it EVERY TIME :( 

Please help!!!

---

### Post by anglican on 2011-03-01
> **wonfineday said:**
> I tried that approach but I need to do it EVERY TIME :( 

Please help!!!Did you pay close attentions to this bit:
> You could also set colors and fonts on the command line or load a session when you run putty (see "man putty").Save the settings you're happy with then load that session each time you run putty:
```
putty -load session
```if you're running putty from the menu then you need to edit the file /usr/share/applications/putty.desktop to change the Exec line to e.g.
```
Exec=putty -load mydefault
```where "mydefault" is the session name containing your chosen fonts/colours.

H

---

### Post by OldManRiver on 2011-07-07
All,

All this "in session" is wonderful, but I want to find the config file and change this for the 20+ sessions I have defined, because the color are not saving correctly for the sessions and I can not see the "blue" on my putty terminal at all.

Thanks!

OMR

---

### Post by OldManRiver on 2011-07-07
All,

Never mind I found them in:

/home/user/.putty/sessions

Got them changed and testing.

Thanks!

OMR

---

