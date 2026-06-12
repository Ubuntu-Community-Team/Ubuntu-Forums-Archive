---
title: "riotball sound doesn't work"
date: 2006-07-09
forum: Gaming &amp; Leisure
---

### Post by DSn0wMan on 2006-07-09
My sound isn't working with riotball. Does anyone know how to fix this?

---

### Post by Perfect Storm on 2006-07-09
Does the sound works on your OS in general?

Try installing libsdl-sound1.2

---

### Post by DSn0wMan on 2006-07-09
> **Artificial Intelligence said:**
> Does the sound works on your OS in general?

Try installing libsdl-sound1.2

Yep it works for everything except riotball. It even works for enemy territories.

---

### Post by Perfect Storm on 2006-07-09
Any error output if you running it from terminal/konsol?

---

### Post by DSn0wMan on 2006-07-09
> **Artificial Intelligence said:**
> Any error output if you running it from terminal/konsol?

Thats the tough part. No error outupt to the terminal.

---

### Post by jISh on 2006-07-09
Try putting this in console first
killall esd

Works for many games.
Just type 
esd
after playing if you want to re-enable it.

---

### Post by DSn0wMan on 2006-07-09
> **jISh said:**
> Try putting this in console first
killall esd

Works for many games.
Just type 
esd
after playing if you want to re-enable it.

Thats the trick! Thanks!

---

