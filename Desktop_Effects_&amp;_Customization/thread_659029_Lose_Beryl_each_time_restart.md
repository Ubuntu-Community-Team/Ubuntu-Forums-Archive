---
title: "Lose Beryl each time restart"
date: 2008-01-05
forum: Desktop Effects &amp; Customization
---

### Post by coachsd on 2008-01-05
I've installed Beryl and it works well. But each time I turn off computer (Dell Inspiron 600m), I have to reinstall Beryl!? Emerald Theme manager is in preferences, but Beryl Diamond Icon is not on toolbar (upper right). I'm running Fiesty Fawn. Do I have to reinstall every time I restart?

Thanks in advance.

---

### Post by b0rka7a on 2008-01-05
just type beryl or beryl-manager in a terminal to start it (i dont remember exactly)
or you can go to System > Preferences > Sessions > Add:
```
name = beryl
command = beryl          #(or beryl-manager)
```

---

### Post by coachsd on 2008-01-05
> **b0rka7a said:**
> just type beryl or beryl-manager in a terminal to start it (i dont remember exactly)
or you can go to System > Preferences > Sessions > Add:
```
name = beryl
command = beryl          #(or beryl-manager)
```

Wow... fast reply! So, yes I do that to restart Beryl each time. So I take it from your response, I must restart Beryl every time I restart my computer? Or is their a way to start and have Beryl already running?

---

### Post by b0rka7a on 2008-01-05
If you add Beryl to System > Preferences > Sessions, it will start automatically every time you start your computer. If you already tried this, and it's not working, try:
```
emerald --replace
beryl --replace
```
and tell me if it worked :)

---

### Post by coachsd on 2008-01-05
It worked... thank you!  :)

---

