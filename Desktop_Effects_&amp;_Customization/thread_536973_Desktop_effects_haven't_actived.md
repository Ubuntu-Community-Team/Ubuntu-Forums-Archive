---
title: "Desktop effects haven't actived"
date: 2007-08-28
forum: Desktop Effects &amp; Customization
---

### Post by omarifr on 2007-08-28
Hi, I'm new in linux ubuntu, I have just installed my ubuntu with innotek virutalbox in my laptop dell insipiron 6400 with video driver ATI Mobility Radeon 1400. I'm  trying to activate the desktop's effects but the screen is in white for a moment and back but the effects didn't active.

I hope that you colud help me with these, thanks.

---

### Post by Chymera on 2007-08-28
if you use compiz fusion type ```
compiz --replace
``` in a terminal.
If that doesn't work it may be due to your ati card... some ati cards are not well supported on linux.

There are ways of getting those ati models that are unsupported working, and you can find some guides here on the forums, but its a heck of a job...

---

### Post by DarkN00b on 2007-08-28
I don't think desktop effects will work on a virtual machine. I could be wrong, but I'm pretty sure 3d acceleration doesn't work inside a virtual machine yet, except for some commercial solutions.

---

### Post by omarifr on 2007-08-29
Thanks for your help, when I execute de code, the screen turn white, all aplications work because I move the cursor and this change because this pass over de buttons. But the screen is always white. Can I Do something more? 



> **Chymera said:**
> if you use compiz fusion type ```
compiz --replace
``` in a terminal.
If that doesn't work it may be due to your ati card... some ati cards are not well supported on linux.

There are ways of getting those ati models that are unsupported working, and you can find some guides here on the forums, but its a heck of a job...

---

### Post by Chymera on 2007-08-30
uhm... i believe that the problem lies with your ati card, search the forums for the name of your card or just something like "ati drivers compiz" ... i have an nvidia card so couldnt give you any personal suggestions, but there are quite a few ppl on teh forums who run compiz on ati models...

---

