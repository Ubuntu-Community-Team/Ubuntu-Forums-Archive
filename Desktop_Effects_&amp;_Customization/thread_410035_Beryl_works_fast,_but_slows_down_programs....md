---
title: "Beryl works fast, but slows down programs..."
date: 2007-04-15
forum: Desktop Effects &amp; Customization
---

### Post by miggols99 on 2007-04-15
I've got Beryl working really well, but some of the programs freeze while I am running Beryl. I have a pretty fast computer, so I do not know why this is happening. I have an ATI radeon X300se if that helps.

EDIT: I'm using the built in driver with AIGLX by the way.

Also, when I type "beryl" into Konsole, I get this:
```
**************************************************************
* Beryl system compatiblity check                            *
**************************************************************

Detected xserver                                : AIGLX

Checking Display :0.0 ...

Checking for XComposite extension               : passed (v0.3)
Checking for XDamage extension                  : passed
Checking for RandR extension                    : passed
Checking for XSync extension                    : passed

Checking Screen 0 ...

Checking for GLX_SGIX_fbconfig                  : passed
Checking for GLX_EXT_texture_from_pixmap        : passed
Checking for non power of two texture support   : passed
Checking maximum texture size                   : passed (2048x2048)

Reloading options

```

---

### Post by aidanr on 2007-04-15
any more specific information on which programs freeze up, for how long, any errors from running them from konsole etc?

the only thing i can think of is that beryl provides visual feedback on programs that freeze up by dimming them, thats something that you don't get with metacity or kwin, so maybe you're just noticing it more because of that?

---

### Post by miggols99 on 2007-04-15
My programs don't dim. For example, when I run Konqueror, it comes up, and the centre is white. If I maximise it, it's fine. Another thing, when I click on the K menu and hover over something, it doesn't change colour! When I run Konsole, I sometimes can't type anything in.

EDIT: Sometimes it runs perfectly :D

---

### Post by serialdae on 2007-04-15
If you run ksysguard or something similar what is pulling the most resources at that time?

---

### Post by miggols99 on 2007-04-15
Well it looks like xorg is taking up the most. One time it was around 90%! Could it be the hardware?

EDIT: When I open up the terminal, the processes do not do much, but Konsole still doesn't let me do anything! I goes up especially when I open up Konqueror, and this is when Konqueror freezes for a bit, then is fine after.

If I maximise a bad program (any I think) it works. Maybe it has something to do with refreshing it?

---

