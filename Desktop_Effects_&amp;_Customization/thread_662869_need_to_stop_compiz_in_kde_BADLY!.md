---
title: "need to stop compiz in kde BADLY!"
date: 2008-01-09
forum: Desktop Effects &amp; Customization
---

### Post by KrotBot on 2008-01-09
i've just been trying to get compiz working on kde with no joy, i tried one command which has left me truly stuffed it was 

compiz --replace ccp & 

how can i undo this i have tried kwin --replace but that ceases to have any effect once i close the terminal, and no compiz starts everytime i reboot. 

If there is terminal command that can undo my mess that would be wkd as all i can do at the mo is access terminal.

Cheers

---

### Post by ajgreeny on 2008-01-09
For a start and assuming you are not going to use compiz for now at least try removing compiz and compiz-core with ```
sudo apt-get remove compiz compiz-core
```then either restart or end the session and restart a new one in kde.  Hopefully it will have worked, though as I am not running kde I am not certain if it will present you with other difficulties of compiz trying to start but not being on the machine.

---

### Post by KrotBot on 2008-01-09
i have gnome on my systme and i use compiz for that so ideally i need to keep compiz on

---

### Post by ajgreeny on 2008-01-09
OK. Sorry, as I don't know kde any more (I used to like it a lot, but before compiz times) I don't think I can help you more.

---

### Post by Forlong on 2008-01-09
Run ```
kwin --replace
``` via [Alt]+[F2] (_not_ in the terminal) and make sure to save the session on logout (KDE does this by default, that's why Compiz runs by default now).

---

### Post by KrotBot on 2008-01-09
cheers guys that should do the trick but in dicking around with it i got compiuz working quite nicley.

---

