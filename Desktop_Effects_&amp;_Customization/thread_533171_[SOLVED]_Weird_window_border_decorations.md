---
title: "[SOLVED] Weird window border decorations"
date: 2007-08-23
forum: Desktop Effects &amp; Customization
---

### Post by Inxsible on 2007-08-23
Attached are the screen shots of the window border decoration under metacity and compiz fusion (installed from Trevino's repos - after he rectified it)

Why are the borders all screwed up under CF. I kinda liked the ones the Human theme have :(

Also the shift switcher plugin doesn't seem to work correctly, I rbr it used to switch between apps like in iTunes album covers, but now it doesnt :(

---

### Post by FuturePilot on 2007-08-23
Looks like you're using Emerald. If you have the Fusion-icon installed switch back to the GTK Window decorator.;)
The shift switcher is still working fine here.

---

### Post by joshuachad on 2007-08-23
I dont know what in the world your talking about. That is the human theme.

---

### Post by joshuachad on 2007-08-23
Oh and yeah you have a plugin enable called 'reflection'. Turn that off and the weirdness will disappear,
Cheers.

---

### Post by Inxsible on 2007-08-23
> **FuturePilot said:**
> Looks like you're using Emerald. If you have the Fusion-icon installed switch back to the GTK Window decorator.;)
The shift switcher is still working fine here.
i dont think i installed emerald at all. but is there a way to switch back to the gtk window decorator without the fusion icon?

if not, i might go and get that fusion-icon deb file

---

### Post by joshuachad on 2007-08-23
if you cant find the icon in menus type press Alt F2 and type fusion-icon to start it. Alternatively to save a step do the same but type metacity --replace to get ur human theme goodness back.

---

### Post by Inxsible on 2007-08-23
> **joshuachad said:**
> Oh and yeah you have a plugin enable called 'reflection'. Turn that off and the weirdness will disappear,
Cheers.Now I don't know what you are talking about :(

Reflection is the plugin to reflect the cube during rotation ..is that what you are talking about?

That has nothing to do with the window borders. My problem is the close /minimize/maximize button. Compare the two screens and you shall see that they are different

---

### Post by Inxsible on 2007-08-23
> **joshuachad said:**
> if you cant find the icon in menus type press Alt F2 and type fusion-icon to start it. Alternatively to save a step do the same but type metacity --replace to get ur human theme goodness back.
Yes metacity --replace does bring back the human theme goodness, but i want that goodness with compiz fusion(like it used to work for me before )

---

### Post by Inxsible on 2007-08-23
FuturePilot, who's repos are you using to have the shift switcher work correctly ?

---

### Post by jocko on 2007-08-23
I guess this is what you're looking for? Hit alt+f2 and run this:
```
gtk-window-decorator --replace
```

---

### Post by Inxsible on 2007-08-23
> **jocko said:**
> I guess this is what you're looking for? Hit alt+f2 and run this:
```
gtk-window-decorator --replace
```

SWEET !!!!!!!

thanks jocko.

Will i have to do this everytime, i start compiz fusion though ?

---

### Post by joshuachad on 2007-08-23
not necessarily. open terminal type 'gconf-editor'. Go to apps >> compiz >> plugins >> decoration and make sure the key entry 'gtk-window-decorator --sync' is there. Also you could go to System >> Prefernce >> Session and add one to run gtk-window-decorator --replace. This will load it everytime you start a gnome session.

---

### Post by Inxsible on 2007-08-23
thanks

---

### Post by FuturePilot on 2007-08-23
> **Inxsible said:**
> FuturePilot, who's repos are you using to have the shift switcher work correctly ?

Trevino's.

---

### Post by joshuachad on 2007-08-23
theres like 2 reflection plugins in my install of compiz. One is cube refelction and one is called i think desktop reflection or window. I can remember the exact name but when i enabled it the windows boders looked just like yours. Oh and at first i only looked at before compiz shot lol. So i was confuesed then i looked at the other and realized what you were saying. hope eveything is running smooth for ya.


Cheers

---

### Post by Inxsible on 2007-08-24
everything runs well. But the shift switcher...is not what it used to be. 

previously, on activation it put all the open windows like we have the albums switch in iTunes. Now all it does is cascade the open windows and make all of them the same size, for eg. my terminal - which i like in small window -- will become as big as my firefox window - which is normally maximised.

I hope I am making sense !

---

