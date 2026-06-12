---
title: "Weird screen artifacts"
date: 2009-05-05
forum: General Help
---

### Post by Anitaviz on 2009-05-05
Ive been getting some wird screen artifacts the last couple of days.

First i thouht i was my graphic card crashing, but after disconvering that they also appear on screen shots, i think it might be somthing else, but i have no idea where to start looking.

They dissapear when i drag my mouse over them or activate a window under them (screen redraws) , but  slowly reapears again in 2-7 seconds.

Hoping somone can help me fix it :)

[http://anitaviz.dk/weird.jpg](http://anitaviz.dk/weird.jpg)

---

### Post by CShadowRun on 2009-05-05
Nice dual screen setup ;)

What graphics card do you have? (*lspci | grep VGA*)
Are you running compiz? (*ps aux | grep compiz*)
Does the problem still occur with compiz disabled? (*metacity --replace*)

You can type the commands inside the bracets to get the answers :)

---

### Post by Anitaviz on 2009-05-05
*lspci | grep VGA:*
VGA compatible controller: nVidia Corporation G72 [GeForce 7300 SE] (rev a1)

[I]ps aux | grep compiz:
Yes running compiz
[/I][I]
metacity --replace[/I]:
Still the exact same error.

Problem started a couple of days ago, and it was working flawlesly before that :(

---

### Post by CShadowRun on 2009-05-05
Hmm, do you have the latest version of the nvidia drivers? (System > Administration > Hardware drivers)

---

### Post by Anitaviz on 2009-05-05
Yes using the latest proprietary drivers.

---

### Post by CShadowRun on 2009-05-05
Try disabling them (so you fall back to the open source "nv" driver)

Does it still happen?

---

### Post by Anitaviz on 2009-05-05
Its at work, and im at home now, so cant check it.

Ill try tomorrow and report back.

---

