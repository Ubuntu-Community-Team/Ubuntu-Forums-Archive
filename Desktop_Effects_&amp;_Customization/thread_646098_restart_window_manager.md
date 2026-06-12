---
title: "restart window manager?"
date: 2007-12-20
forum: Desktop Effects &amp; Customization
---

### Post by Hybrid86 on 2007-12-20
I am running gutsy with compiz fusion built in. Occasionally, for no reason, my skydome will just go black and nothing I do short of a restart will bring it back. When this happened on feisty, I would just right click on  the beryl icon, hit "restart window manager", nd the problem would be solved.
Compiz fusion however has no icon, so that solution is pretty much gone.

Long story short, how do I restart my window manager (compiz fusion) in gutsy?

---

### Post by delphiguy on 2007-12-20
Try this
Ctrl+Alt+Backspace

and see if this is what you are looking for,  it will restart X.

---

### Post by Espreon on 2007-12-20
You need to compile the CF Icon... You can look at my guide for installin CF from GIT (CF Icon included). Installin CF from GIT may eleminate the problem.

---

### Post by Hybrid86 on 2007-12-20
Ctrl+Alt+Backspace worked, but it also logged me out. I'd just like a simple way to restart the window manager like I used to be able to do with beryl, and without installing additional software.

I know the option/command must exist. Is there some type of command I can put into the terminal?

---

### Post by schauerlich on 2007-12-20
Have you tried ```
compiz --replace
``` ?

---

### Post by Espreon on 2007-12-21
> **Hybrid86 said:**
> Ctrl+Alt+Backspace worked, but it also logged me out. I'd just like a simple way to restart the window manager like I used to be able to do with beryl, and without installing additional software.

I know the option/command must exist. Is there some type of command I can put into the terminal?

Yeah but the solution in Beryl you spoke of (the Beryl Menu) is additional software.
CF Icon is basically the CF equivalent of the Beryl Menu.

---

### Post by FuturePilot on 2007-12-21
To go back to Metacity
```
metacity --replace
```
To go back to Compiz
```
compiz --replace
```

It's best to put those commands into Alt+F2 instead of a terminal because when you close the terminal it will usually close whatever was running in the terminal at the time.

---

