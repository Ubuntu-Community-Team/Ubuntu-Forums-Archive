---
title: "My RIght Cick Stopped Working"
date: 2010-02-12
forum: Desktop Environments
---

### Post by fastop on 2010-02-12
It was working fine, then one day I booted up my computer and I just couldnt right click, its rather annoying! Has this problem ever came up before? What can I do to solve it?
Thankyou:p

---

### Post by ajgreeny on 2010-02-12
Use ```
xev | grep ', button'
``` in terminal and in the box that appears use a right click with your mouse.  You should get an output something like
    ```
state 0x10, button 3, same_screen YES
    state 0x410, button 3, same_screen YES
```
in the terminal, but if not, then it may be a mouse hardware fault, or at least the system not recognising the click in some way.

---

### Post by fastop on 2010-02-13
when I do that and left click i get...

state 0x10, button 1, same_screen YES
state 0x110, button 1, same_screen YES

nothing comes up with right click.

Any advice on this?

---

### Post by ajgreeny on 2010-02-13
Seems most likely that the mouse is faulty.

Try borrowing another mouse to try just to make sure, but no point going through hoops for something as cheap as a mouse, surely?

---

### Post by fastop on 2010-02-13
nah its not worth it really haha :) just didnt wanna get rid of this mouse as its nice, but i guessed it was faulty after that test, i found a random one and that works fine. thankyou :)

---

