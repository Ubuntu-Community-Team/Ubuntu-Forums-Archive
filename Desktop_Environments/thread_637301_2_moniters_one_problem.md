---
title: "2 moniters one problem"
date: 2007-12-10
forum: Desktop Environments
---

### Post by James42 on 2007-12-10
I just got Ubuntu 7.10 and after installing updates and what not i installed my ATI drivers from the documentation page, i also tried to get some compiz affects going and finally i was attempting this one two monitors with little knowledge of the inner workings of this OS.  Now i have this problem were when ever i start my computer Ubuntu boots up and then right at the point were i would login the main monitor goes black and the second goes a peachish orange color, and you can login and everything just you cant see anything and if you move he mouse over to the second screen it is just a white block.Is there some kind of safe mode i can enter to undo some of this? or should i just format and start over? Btw my system specs are X2 4200 CPU and a X1600 GPU.

---

### Post by wankel on 2007-12-11
Not a real solution for you, but it should bring your system in a workable state again if only Compiz is to blame.

Once you got into the situation that you describe, follow these steps:
* press ALT+CTRL+F2
* give your username at the prompt
* type your password
* type "ps | grep compiz" (no "'s)
* kill "the number at the start"
* type "ps | grep emerald" (no "'s)
* kill "the number at the start"
* press ALT+F7

If Compiz is misbehaving on my system, this way I can be quite sure it stops. Below some more explanation:

* press ALT+CTRL+F2
On your system, Ubuntu starts six text mode sessions and one graphical session by default. For desktop use, the graphical (or X) session is most convenient, but often the text mode consoles come in handy. The screen will only have an invitation to login to start with, except for the console found on F1.
* give your username at the prompt
* type your password
There will be no stars or bullets; if you make a mistake, just press backspace long enough or press enter to start over with your username.
* type "ps | grep compiz" (no "'s), like:
wbk@triacer:~$ ps  | grep ompiz
 8398 pts/3    00:00:00 compiz
 8473 pts/3    00:01:55 compiz.real
* kill "the number at the start", like:
kill 8398 8473
* type "ps | grep emerald" (no "'s)
* kill "the number at the start"
Same way as for compiz
* press ALT+F7
This will bring you back to the graphical session. It should remember automatically not to start Compiz, once you log out or restart your computer.


Good luck!

(by the way, many more users pose questions about Compiz. Although not all of them use multiple screens and ATI drivers, I am sure others will have discussed it before. Did you try searching the forum?)

---

