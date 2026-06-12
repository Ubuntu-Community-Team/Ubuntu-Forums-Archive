---
title: "ubuntu 8.10 not restarting"
date: 2009-02-13
forum: General Help
---

### Post by errolgreer on 2009-02-13
****I have just installed 8.10, having had no problems with 8.04. I now find that on selecting shut down or restart I have to press the reset button instead of the computer doing so itself. Is this a known bug in 8.10 or if not, how do I fix this ?

Many thanks
Errol

---

### Post by x33a on 2009-02-13
try sudo shutdown -r in a terminal for restart.

---

### Post by theozzlives on 2009-02-13
Are you using the fast user switcher, or the shutdown icons in the Ssystem menu?

---

### Post by errolgreer on 2009-02-13
Using the red icon at the top right and then clicking on restart.

---

### Post by errolgreer on 2009-02-13
> **x33a said:**
> try sudo shutdown -r in a terminal for restart.

Tried that, but I get the same result. ie sreen goes black with a small flashing white cursor at upper left, and stays that way until I press the start button on the box !

---

### Post by x33a on 2009-02-13
i think it might be caused due to alsa. i have seen a lot of people reporting the same problem and i thought it might have been fixed by now.

take a look here:

[https://answers.launchpad.net/ubuntu/+question/49799](https://answers.launchpad.net/ubuntu/+question/49799)

---

### Post by errolgreer on 2009-02-15
> **x33a said:**
> i think it might be caused due to alsa. i have seen a lot of people reporting the same problem and i thought it might have been fixed by now.

take a look here:

[https://answers.launchpad.net/ubuntu/+question/49799](https://answers.launchpad.net/ubuntu/+question/49799)

Many thanks, works like a dream ! I'm really surprised that a bug like that got through testing!

Errol

---

