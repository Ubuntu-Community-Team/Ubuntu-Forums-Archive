---
title: "lil help with my Graphics Card"
date: 2007-07-13
forum: Desktop Effects &amp; Customization
---

### Post by Lunatrix on 2007-07-13
i have a ATI Radeon 9550, i went into the restricted drivers, installed my ATI Driver, and i had to restart my comp. and now i can login. but i just get a tan screen, cant see anything on my desktop. just my mouse, anything i can do?

---

### Post by Lunatrix on 2007-07-13
i also installed compiz fusion too before i restarted

---

### Post by Lunatrix on 2007-07-13
anything plz?

---

### Post by bdtgp on 2007-07-13
try hitting ALt+F2 and running 
```
compiz --replace
```

That should give you your taskbar back.

---

### Post by Lunatrix on 2007-07-13
ok, ill try that.

---

### Post by Lunatrix on 2007-07-13
ok, i also used your tut to install compiz, but i cant seem to get anything working, (Cube,spinning effects, or ANYTHING else that comes with compiz. help plz?

---

### Post by bdtgp on 2007-07-13
A lot of those effects are dependent on your video card.  Since I am not running an ATI (Mine is an NVIDIA), I'm not sure if the fixes are the same.  If you have Emerald Themes then you can try 
```
compiz --replace -c emerald &
``` 
A lot of times some of the effects will randomly start working after using that command.

If you're up for another fix that I'm really not sure about you can add these lines to xorg file device section (video card):
```
Option "RenderAccel" "True"
Option "AllowGLXWithComposite" "True"
Option "backingstore" "True"
Option "TripleBuffer" "True"
```

And then at the end add this:
```
Section "Extensions"
    Option "Composite" "Enable"
EndSection

```

---

