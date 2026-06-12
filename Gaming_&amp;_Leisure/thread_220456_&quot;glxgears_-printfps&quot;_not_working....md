---
title: "&quot;glxgears -printfps&quot; not working..."
date: 2006-07-21
forum: Gaming &amp; Leisure
---

### Post by PriceChild on 2006-07-21
Not sure why this has disappeared :(

glxgears -printfps and the acknowledging not a benchmark one doesn't work either.


Anyone got any ideas?

---

### Post by reacocard on 2006-07-21
it's not working for me either. but if i run glxgears without any arguments, it gives me the fps anyway. :-k

---

### Post by vem0m on 2006-07-21
hmmmmmm i dunno mine works

---

### Post by codejunkie on 2006-07-21
have either of you installed compiz/xgl recently? i noticed that when i used quinns compiz packages it broke glxgears.

---

### Post by User_Program on 2006-07-21
Try just typing 

> glxgears 

I think the -printfps was taken out.

---

### Post by vem0m on 2006-07-21
-printfps works for me

---

### Post by PriceChild on 2006-07-21
Yeah i've got xgl compiz

Just noticed that fps are printed... just takes a while between each one.

THanks

---

### Post by reacocard on 2006-07-21
yep, I use compiz too.

---

### Post by mkw87 on 2006-07-25
Hmm, mine wont print the FPS using -printfps or not using it, and I do not have xgl/compiz (I tried it with a fresh install of dapper and it didnt work?).

---

### Post by nwgray on 2006-07-25
Try this, it worked for me:

glxgears -iacknowledgethatthistoolisnotabenchmark

---

### Post by mkw87 on 2006-07-25
> **nwgray said:**
> Try this, it worked for me:

glxgears -iacknowledgethatthistoolisnotabenchmark
Its not necessarily being used as a benchmark, its something to test if opengl acceleration is working.

---

### Post by malathia on 2006-12-26
> **mkw87 said:**
> Its not necessarily being used as a benchmark, its something to test if opengl acceleration is working.

That was a serious suggestion. That command is also known to work like glxgears -printfps.

You should be happy that you're not having the problem that I just started having. Everytime I try to run glxgears I get automatic "Killed."
Still researching that one.

---

