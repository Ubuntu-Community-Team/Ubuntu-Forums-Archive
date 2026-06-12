---
title: "Beryl kinda dead..."
date: 2007-09-12
forum: Desktop Effects &amp; Customization
---

### Post by culmor30 on 2007-09-12
Well, I installed Beryl, and it was working fine. So I decided to screw with the settings being the way I am, and set the graphics to be forced... something. But now whenever Beryl starts it completely DIES and I have to CTRL-ALT-Backspace. I tried reinstalling Beryl to no avail. Anyone know how I can restore it default without opening it? I can still get into the settings managers.

Thanks much...
culmor30

EDIT: Btw, I'm very, VERY new to Linux. About a billion years of windows experience though :P.

---

### Post by FuturePilot on 2007-09-12
Quit beryl-manager. Open your home folder and press Ctrl+H to show the hidden files, then delete the .beryl-managerrc file
That will reset beryl-manager to the default settings

---

### Post by culmor30 on 2007-09-12
Ah, that worked, thanks much. Back to configuration - those settings...

---

### Post by culmor30 on 2007-09-13
Okay, two more questions, one related to Beryl.

1. I get black edges around windows after moving or resizing them. Some way to fix this? Pretty annoying. I have a good graphics card so there shouldn't be an issue.

2. How do I disable that annoying tap-to-click crap on my touchpad? Makes typing like... being pecked to death by a duck.

---

### Post by hyperair on 2007-09-13
1. Disable blur.
2. No idea.

---

### Post by culmor30 on 2007-09-13
Thanks, 1 worked. As for 2 I actually don't care... and one more Baryl thing, when I press the mapped SHIFT+F9 I don't get rain like I'm supposed to. Some way to override its graphics protection?

---

### Post by FuturePilot on 2007-09-13
Some cards don't have the necessary pixel shader required to run the rain effects.

---

### Post by culmor30 on 2007-09-13
But there's not an error or warning or anything?

---

### Post by eentonig on 2007-09-13
Anyway, you should abandon Beryl, as it's a dead project.

They have merged with Compiz to offer you Compiz Fusion.

---

### Post by FuturePilot on 2007-09-13
> **culmor30 said:**
> But there's not an error or warning or anything?

If you start Beryl from the terminal and try to start the water effects you should get an error.

---

### Post by culmor30 on 2007-09-13
I am a linux n00b. I DO know how to start the terminal, but how to use it at all escapes me.

---

### Post by FuturePilot on 2007-09-13
First switch back to Metacity from Beryl Manager. Then quit Beryl Manager. Then open a terminal and type
```
beryl-manager
```
Then with Beryl Manager switch back to Beryl. Then try the water effects. Keep the terminal open while doing this.

---

### Post by culmor30 on 2007-09-13
Still just nothing :\

---

### Post by FuturePilot on 2007-09-13
I'd hate to ask the obvious, but are the water effects enabled?

---

### Post by culmor30 on 2007-09-13
Hah... I'm not that much of a noob.

---

### Post by FuturePilot on 2007-09-13
Ah, now I remember. Only the early versions of Beryl used to give an error when started from the terminal if your card couldn't use the water effects. The newer versions don't do that anymore though. Most likely if it's not working, then your card can't handle it.

---

### Post by culmor30 on 2007-09-13
Eh... too bad. Zoom doesn't seem to work either but I'm not too fussy about it, I have a desktop cube :D

---

### Post by hyperair on 2007-09-14
Whaaat..? Zoom doesn't work? What happens when you activate it?

---

