---
title: "kbackgroundsnapshot -c does not work (for capturing current window)"
date: 2013-05-14
forum: Desktop Environments
---

### Post by jazzgossen on 2013-05-14
I have noticed that "kbackgroundsnapshot -c" to capture a screenshot of the current window does not work in Kubuntu 12.10 or 13.04. At least not with my computer. I only get a corrupted or blank PNG image. I also get the terminal output 

X Error: BadDrawable (invalid Pixmap or Window parameter) 9
   Major opcode: 62 (X_CopyArea)
   Resource id: 0x0

I filed a [bug report at launchpad]("https://bugs.launchpad.net/ubuntu/+source/ksnapshot/+bug/1135350") but nobody seemed to notice it there.

Does kbackgroundsnapshot work for anybody else?

---

### Post by oldos2er on 2013-05-14
I get the same error. Posted on launchpad too.

---

### Post by Glynnux on 2013-05-14
Perhaps you could install 'scrot' from the software centre. 
To take a screenshot you need to open a terminal and type " scrot -d 5 " (note 5 indicates a countdown and is a variable so you can change the 5 to however many seconds delay you prefer before the pic is taken.
You can even specify where the pic is saved. The above suggestion will save to 'Home'.
You can specify "scrot -d 4 desktop.jpeg" which will wait 4 seconds before taking a screenshot and saving it to the desktop in jpeg format.
Likewise "scrot -d 6 desktop.png".... wait six seconds to take the screenshot in png format.
I've also tried "scrot -d 5 drive.ferrari" but it either didn't work or I have to specify my own drive (joke)

---

### Post by jazzgossen on 2013-05-15
Thanks for the tip! "scrot -ub" does exactly what I want.

I'll mark the thread as solved even though kbackgroundsnapshot still doesn't work.

---

