---
title: "Random Restarts?!"
date: 2006-09-08
forum: Desktop Environments
---

### Post by suhaib on 2006-09-08
My GUI resets whenever it feels like it.  It's getting a bit annoying (as you can imagine), since you never know when it's going to happen!  I've lost plenty of unsaved data (or recent changes) because of it.  

Does anyone know why this may be occuring?

Thanks.

---

### Post by artinla on 2006-09-08
I am confused, if it is only the Graphical User Interface that restarts, why are you losing data?   

If the computer itself is restarting, then I would suspect the power supply is going bad.  That is a classic symptom of low 5V.

---

### Post by suhaib on 2006-09-09
I'm losing unsaved data because I may be writing an email or a report and boom!  GUI resets.  Not the actual system.  So after resetting it brings me straight back to my desktop, logged in, wireless connection already established, but no applications on my taskbar.

**EDIT:  **I may have been hitting <Shift + BackSpace> which disables xgl.  So I disabled the key binding in the terminal by typing the following.  I then added the same command to my start-up sessions.

```
xmodmap -e keycode 22 = BackSpace
```

**EDIT 2:  **Ok adding that line to the start-up sessions didn't do nothing.

---

