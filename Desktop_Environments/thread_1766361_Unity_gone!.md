---
title: "Unity gone!"
date: 2011-05-24
forum: Desktop Environments
---

### Post by Jomukuk on 2011-05-24
I installed 11.04.
No problems.
The launcher icons were too big so i resized them with compiz.
Being a fiddler I played with the thing for a while, no problems until I unticked desktop wall, when the entire desktop departed. Is there any way short of a re-install to get thi gs working again ?

---

### Post by Copper Bezel on 2011-05-24
Yeah, the Unity plugin depends on the Wall. I think the simplest way would be to hit Ctrl+Alt+T, run ccsm, and revert your changes (by re-enabling the Wall and Unity.) Otherwise, you can reset your Compiz settings wholesale (from the last link in my sig):

```
gconftool-2 --recursive-unset /apps/compiz
gconftool-2 --recursive-unset /apps/compiz-1
gconftool-2 --recursive-unset /apps/compizconfig-1
unity --reset
```

---

### Post by Frogs Hair on 2011-05-24
Hi and Welcome 

Try restarting the computer . When I was getting my cube running in Unity I had the same thing happen and all was well after reboot.

---

### Post by Jomukuk on 2011-05-24
Thankyou all. Unity back...I did a reset!
Lifesaver !

---

### Post by Copper Bezel on 2011-05-24
Excellent. = ) Just mark the thread as Solved if you would, Thread Tools in the upper right.

---

