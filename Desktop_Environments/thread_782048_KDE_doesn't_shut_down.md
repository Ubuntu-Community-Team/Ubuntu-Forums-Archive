---
title: "KDE doesn't shut down"
date: 2008-05-04
forum: Desktop Environments
---

### Post by krojew on 2008-05-04
I have a problem with shutting down from KDE. When I click on the shutdown button the screen turns black. I can still see and move the cursor but nothing happens. I can only do shutdown -h now. Can anybody help?

---

### Post by MickS on 2008-05-04
I have the same problem, killing X is the same, still haven't found a solution other than sudo halt which is a pain.

Mick

---

### Post by TheMemphisExperience on 2008-05-04
I had a hard time shutting down 8.04 with KDE 4 from the liveCD. Pressing the power button triggered a line that said "halting all operations(or processes or something)...for NOW". 

I don't think KDE or Kubuntu are for me. I will probably do a fresh Ubuntu install on my laptop if Xubuntu does not meet my approval. It saddens me...but I can't figure out my present Ubuntu problem. And it crashes when I try to play Torus Trooper. Oddly, on on my laptop. 

Anyway, maybe the third try with Kubuntu will be the one that enamors me with it. I'm not holding my breath.

---

### Post by angry_johnnie on 2008-05-05
Does it happen when you click on the button that says **log out**, in your menu? Or is it after that, when clicking on the **Turn Off** option?

If you click on log out, and then it goes black, you could still try hitting Alt + T (T as in Turn Off), and that would do it.

If that doesn't do it, you could add a custom launcher to your kicker panel, with the command **kdesu /sbin/poweroff**.

Of course, launching that command from the kicker panel would still ask you for your password, but it's still quicker than opening a terminal and telling it to sudo shutdown -h now.

---

### Post by krojew on 2008-05-05
It's after clicking the Turn off button (I'm not sure if that's its exact name in English). The same thing happens after clicking Reboot.

---

