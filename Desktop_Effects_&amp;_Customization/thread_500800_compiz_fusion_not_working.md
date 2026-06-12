---
title: "compiz fusion not working?"
date: 2007-07-14
forum: Desktop Effects &amp; Customization
---

### Post by Lunatrix on 2007-07-14
i got a ATI Radeon 9550, i installed compiz. everything is running fine, but the compiz functions are not active, anyway how to turn them on?

---

### Post by Lunatrix on 2007-07-14
plz? anything?

---

### Post by Lunatrix on 2007-07-14
hello?!?!??!?!

---

### Post by Lunatrix on 2007-07-14
Cmon Man!!!!!!

---

### Post by dreadlord_chris on 2007-07-14
> **Lunatrix said:**
> i got a ATI Radeon 9550, i installed compiz. everything is running fine, but the compiz functions are not active, anyway how to turn them on?

open a terminal and type in:
```

compiz --replace

```

What happens?

---

### Post by Lunatrix on 2007-07-15
Fatal: Failed test: texture_from_pixmap support
Checks indicate that it's impossible to start compiz on your system.


i do not like that error at all.

---

### Post by Lunatrix on 2007-07-15
does that mean that i can never run compiz?

---

### Post by Lunatrix on 2007-07-15
hello? i need some answers here i also have AIM

---

### Post by AlexenderReez on 2007-07-15
have you enable your graphic card support ?and install its driver?

---

### Post by Lunatrix on 2007-07-15
i used envy, it did it for me i guess

---

### Post by AlexenderReez on 2007-07-15
hm....envy only help you to install driver not to setting it....search in tips and tutorial section how to enable your card support...i think pricechild already wrote about it...i never use envy...manual installation is even better...

---

### Post by Lunatrix on 2007-07-15
i tryed manual installation, my login screen didnt load up.

---

### Post by dreadlord_chris on 2007-07-15
> **Lunatrix said:**
> Fatal: Failed test: texture_from_pixmap support
Checks indicate that it's impossible to start compiz on your system.


i do not like that error at all.

Now, that's not all it said.... I need you ro actually post the output from that command...

---

### Post by ShdwNova on 2007-07-20
I have a friend with a Radeon 9550 and the exact same problem. Compiz-fusion is installed using Trevino's git repo's.  The output of compiz --replace is 
```
Fatal: Failed test: texture_from_pixmap support
Checks indicate that it's impossible to start compiz on your system.
```
The ATI driver is installed through the Restricted Drivers Manager. It seems to work as glxgears works and posts a good framerate. 
There is probably already a guide for this, but I can't seem to find it. Does anyone have a link/ideas?
Thx in advance.

---

### Post by maxrisc on 2007-07-24
It doesn't work on Mobility 9600 either.  I get the same error.

Beryl ran on it a couple of months ago but I have not been able to run Compiz.(CompComm)

I've used Envy to load the ATI Proprietary driver as it gets better frame rates than the OS FGLRX driver.
FGLRX Driver gives me the same error as well.

---

### Post by Spam Banjo on 2007-07-30
Bump.


This sucks. I had Beryl running under XGL, and Compiz just didn't work, although I keep trying. After updating today I get the same message. WTF?

Any Ideas?

---

