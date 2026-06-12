---
title: "2 problems concerning multimedia keys..."
date: 2008-06-15
forum: Desktop Environments
---

### Post by MJBoa on 2008-06-15
I have two things that I want to change with my keyboard.
First of all I want to change the volume step so that when I hit volume increase or decrease it doesn't change the level so dramatically. It goes from deafeningly loud to too quit in three presses.
Second, how can I make certain keys respond while they're pressed down. I mean obviously, the character keys already do this but I want to be able to just hold down the volume buttons. I know this is possible I remember reading something about when I was figuring out how to map keys.
Any help would be appreciated, thanks.

---

### Post by p_quarles on 2008-06-16
The minimum volume step is, I think, an attribute of the sound hardware. The output of the following might shed some light:
```
amixer | grep -5 Master
```

---

