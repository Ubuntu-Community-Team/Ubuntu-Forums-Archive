---
title: "Quick Question"
date: 2007-04-17
forum: Gaming &amp; Leisure
---

### Post by Harkainos on 2007-04-17
I am planning on installing WoW to my Ubuntu 6.1 OS. I have everything in order (Video/Wine) and will be using the tutorial posted on the forums.

I already have WoW installed in the windows partition.

My question is this: 
Having TBC, should I copy both the Original and TBC into the same folder, then run the installer? 
Could I just put the original in and install that, then copy all the files from the windows partition to the wine section? 

or

Could I just run WoW from my windows partition using Wine?

Thanks in advance.

---

### Post by MurnShaw on 2007-04-17
Based on my experience you can probably just run it from your windows partition. I don't know that for sure, but I think so. I DO know that if you just drag the wow folder into .wine/drive_c/program files/ it will work as is.

---

### Post by Harkainos on 2007-04-17
How would I, then, edit registry files for it... per the tutorial?


Does this process work with most games?

---

### Post by MurnShaw on 2007-04-17
> **Harkainos said:**
> How would I, then, edit registry files for it... per the tutorial?


Does this process work with most games?

Uh when you edit the registry it affects the wine emulation shell, not the program. You just need to type regedit in terminal to edit it. The way I understand how wine works is it sets up a pseudo VM that runs a custom version of windows which runs the program, so yes, the process works with most games.

Please correct me if I'm wrong.

;-)

---

### Post by Harkainos on 2007-04-17
is the registry universal then? because if i install in windows that is where the registry is edited....

---

### Post by MurnShaw on 2007-04-17
Yes, yes it is.

---

### Post by Harkainos on 2007-04-17
LOL.... great response. LOL

---

