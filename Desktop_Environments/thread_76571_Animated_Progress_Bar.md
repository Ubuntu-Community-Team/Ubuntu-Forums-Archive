---
title: "Animated Progress Bar"
date: 2005-10-15
forum: Desktop Environments
---

### Post by pccampos on 2005-10-15
Hi Ubuntu Folks,


I noticed that the cool animation on the progress bar from Clearlook theme is gone, since a few updates on breezy. How can I bring this features back, I got used to it and now something always seens wrong.



Thanks, Pedro

---

### Post by marekm on 2005-10-15
In my opinion You have to recompile clearlooks engine with option --enable-animation, and of course install it into Your system :)

---

### Post by bvc on 2005-10-15
open the themes gtkrc and make sure
progressbarstyle  	= 0
```
engine "clearlooks"
   {
    menubarstyle      	= 2       # 0 = flat, 1 = sunken, 2 = flat gradient
    menuitemstyle     	= 1       # 0 = flat, 1 = 3d-ish (gradient), 2 = 3d-ish (button)
    listviewitemstyle 	= 1       # 0 = flat, 1 = 3d-ish (gradient)
    progressbarstyle  	= 0       # 0 = candy bar, 1 = flat
  }
}
```

---

### Post by bvc on 2005-10-15
[QUOTE=marekm]In my opinion You have to recompile clearlooks engine with option --enable-animation, and of course install it into Your system :)[/QUOTE]Oh, I didn't think of that. They disabled it? Bummer!

---

### Post by WorLord on 2005-10-26
Does anyone have any idea why this was disabled?  That's a pity, it was a very awesome effect.

---

### Post by iimess on 2005-11-03
[QUOTE=bvc]open the themes gtkrc and make sure
progressbarstyle  	= 0
```
engine "clearlooks"
   {
    menubarstyle      	= 2       # 0 = flat, 1 = sunken, 2 = flat gradient
    menuitemstyle     	= 1       # 0 = flat, 1 = 3d-ish (gradient), 2 = 3d-ish (button)
    listviewitemstyle 	= 1       # 0 = flat, 1 = 3d-ish (gradient)
    progressbarstyle  	= 0       # 0 = candy bar, 1 = flat
  }
}
```[/QUOTE]

Mine is set to 0, progress bar isn't flat but just won't animate.
Also I notice that when charging the battery the AC Plug icon won't animate either.
The minimize animation that I don't want is still there though...

---

### Post by stubby on 2005-11-12
Perhaps this would help shed some light [http://www.ubuntuforums.org/showthread.php?t=89056&highlight=clearlooks]("http://www.ubuntuforums.org/showthread.php?t=89056&highlight=clearlooks")

---

