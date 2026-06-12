---
title: "Compiz leaves me stuck @ Dimmed password Screen"
date: 2007-08-02
forum: Desktop Effects &amp; Customization
---

### Post by hardKNOXbz on 2007-08-02
hello friends....
Compiz fusion has been working for me very well without a hitch until now......
Everytime the security password screen appears, when trying to install updates, i enter password, click OK and nothing happens... the little password box disappears and i am stuck at the dimmed screen....  

I then have to do alt+ctrl+backspace to come out and sign in again.... i know it's compiz because when i do ```
metacity --replace
``` and go to the same screen there is no problems

any ideas  guys? thanks in advanced

---

### Post by Deco_21 on 2007-08-02
Its about your XGL Session, you should try to make another one, try this. 

[HTML]http://ubuntuforums.org/showthread.php?t=488385&highlight=ati+compiz[/HTML]

Find the part where makes the XGL Session , but try to make another with some different name ok.

---

### Post by crimesaucer on 2007-08-02
> **hardKNOXbz said:**
> hello friends....
Compiz fusion has been working for me very well without a hitch until now......
Everytime the security password screen appears, when trying to install updates, i enter password, click OK and nothing happens... the little password box disappears and i am stuck at the dimmed screen....  

I then have to do alt+ctrl+backspace to come out and sign in again.... i know it's compiz because when i do ```
metacity --replace
``` and go to the same screen there is no problems

any ideas  guys? thanks in advanced

This happened to me for a while until it recently fixed it's self in one of the updates.


The way you can fix this (without really fixing it), is if you type "alt+f2" and enter:

```
gconf-editor
```

then click:

 apps-->--gksu

then in the area on the right, check the box called "disable-grab"


This will disable the "dimmed" grab screen, it will just give you a regular password box with no "dimmed" screen.


However, this is not got for security...which is why the grab screen exists.


I disabled my grab screen for a while so I could enter passwords without getting frozen on the dimmed grab screen, then I un-checked it just a few days ago and it worked for me again.

---

### Post by coolen on 2007-08-03
Ooh, very handy.
I've been having the same issue. I never much cared for the screen grab, anyways. Every so often it interrupts me when I'm working, and that makes me sad...
Just wondering, from a security standpoint, how is this a security issue?

---

### Post by crimesaucer on 2007-08-03
It has something to do with your password being typed and being able to be compromised...but I'm not sure exactly how. I disabled my grab for over a month, I don't really have anything to hide on my computer...no credit card or bank info.

---

### Post by coolen on 2007-08-03
Ahh, I see. That makes sense, I guess.
Until I find a better workaround, though, I may have to take the risk.
All I have on my computer are several personal confessions to heinous crimes committed in my area over the past few years. They're between me and the Lord...

---

### Post by crimesaucer on 2007-08-03
lol.

---

### Post by hardKNOXbz on 2007-08-03
i've re-install XGL and it doesnt seem to happen again..... thanks Deco_21, and thanks crimesaucer....

i wanted to know how to disable that, reminded me of Vista's UAC that people like to complain about

---

