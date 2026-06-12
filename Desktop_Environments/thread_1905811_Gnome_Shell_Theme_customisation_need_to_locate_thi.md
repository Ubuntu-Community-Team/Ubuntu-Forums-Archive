---
title: "Gnome Shell Theme customisation: need to locate this setting"
date: 2012-01-07
forum: Desktop Environments
---

### Post by bra|10n on 2012-01-07
I have been slowly tweaking my GS theme but cannot find 1 last thing. I have changed the caps settings in the search overview headings but can't find the 1 for "SETTINGS". Can anybody point me in the right direction?

---

### Post by BlinkinCat on 2012-01-07
Do you mean the System Settings under your name on the right hand corner? - :)

---

### Post by bra|10n on 2012-01-07
Sorry no. SETTINGS just to the left of the mouse pointer

---

### Post by BlinkinCat on 2012-01-07
"Advanced Settings" comes up as an application if installed - Did you install the tweak tool?

---

### Post by cbowman57 on 2012-01-07
Open up alacarte & edit the properties of the SETTINGS sub-menu to Settings, or whatever you want to call it.

---

### Post by bra|10n on 2012-01-07
Thanks, but I think you misunderstand. I want to change the uppercase text "SETTINGS" in the shell itself. 

You can see I have changed "Applications" and "Places & Devices" already. 
I found these in .js files located in /usr/share/gnome-shell folder, but can't find any reference to the SETTINGS that you see in the screenshot.

---

### Post by BlinkinCat on 2012-01-07
I apologize - I misread the situation.

I don't know how to do that

---

### Post by bra|10n on 2012-01-07
> **cbowman57 said:**
> Open up alacarte & edit the properties of the SETTINGS sub-menu to Settings, or whatever you want to call it.

Thank you however this is not an application name I want to alter. It must be a GS file surely.
cheers

---

### Post by bra|10n on 2012-01-07
> **BlinkinCat said:**
> I apologize - I misread the situation.

I don't know how to do that

No apology necessary. Thank you regardless

---

### Post by Frogs Hair on 2012-01-07
The font in the Gnome Shell theme is set in the gnome-shell.css that would be in the theme folder unless it was download and installed separately .

Does caps = capital letters ?

---

### Post by bra|10n on 2012-01-07
Frogs Hair cheers but it is not the font, but rather the uppercase or caps I want to modify. SETTINGS is the only instance of uppercase anywhere in the shell remaining.

---

### Post by cbowman57 on 2012-01-07
Did you already scan appDisplay.js ?

---

### Post by bra|10n on 2012-01-08
> **cbowman57 said:**
> Did you already scan appDisplay.js ?

Indeed I had: only I thought I'd check it again thanks to you and behold, there it was.
cbowman57 thank you very much :D

---

### Post by cbowman57 on 2012-01-08
> **bra|10n said:**
> Indeed I had: only I thought I'd check it again thanks to you and behold, there it was.
cbowman57 thank you very much :D

Took me a bit to figure out exactly what it was you were doing/already changed. 

Glad that did it. :)

---

