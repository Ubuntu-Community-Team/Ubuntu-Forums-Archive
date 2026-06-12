---
title: "display problem"
date: 2009-03-20
forum: General Help
---

### Post by sheshdd on 2009-03-20
Ok,so here's the deal:
Today i turned on my computer and the Ubuntu Log On screen was HUGE!I logged on and tried to change the resolution from the current 640x480 to a higher one,but theres no way to do that,all the modes displayed are lower.Then i got a system message about restricted drivers.It seems someone else who uses this computer activated those,but they simply don't work,how can i stop using this restricted driver(for my geforce mx 400)and use the default display ubuntu comes with?

---

### Post by sheshdd on 2009-03-20
bah,just fixed it,so nevermind,sorry for yet another useless thread.

---

### Post by kestrel1 on 2009-03-20
The restricted drivers do work, but they take a bit of configuring in 8.10

---

### Post by sheshdd on 2009-03-20
well,i figured it out,opened the nvidia config(gksudo nvidia-settings),set the screen resolution from there and saved the xorg file.The problem i'm having now is with the desktop effects,when i select "normal" or "extra",i lose the upper part of the windows,where the title and maximize,close,minimize buttons are(of every aplication BTW).

---

### Post by kestrel1 on 2009-03-21
Try this from a terminal```
gconftool-2 -s '/apps/metacity/general/compositing_manager' --type bool true
```

---

### Post by sheshdd on 2009-03-24
didn't work,actually it's worse now,the message displayed is "cant activate desktop effects",it actually doesn't even switch to the "normal" mode,it just stays without any effects at all.jeez

EDIT:
And when i change workspaces i dont get that temporary demostrative image that shows how i'm changing workspaces.

think i'll have some ice cream...yes i will...

---

### Post by sheshdd on 2009-03-24
still can't figure this out,has anyone had this problem before?

---

