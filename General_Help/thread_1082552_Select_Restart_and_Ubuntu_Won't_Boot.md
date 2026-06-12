---
title: "Select Restart and Ubuntu Won't Boot"
date: 2009-02-27
forum: General Help
---

### Post by Lunx on 2009-02-27
Having a problem restarting computer from desktop. If I select restart my puter closes down and fires up only as far as first splash screen, doesn't get to boot screen. If I select shutdown and then switch on manually I have no dramas, everything boots as normal. Any suggestions as to what could be the trouble?

Running 8.10

---

### Post by iaculallad on 2009-02-27
Does doing it from the terminal outputs the same error?

```
sudo shutdown -r now
```

---

### Post by Lunx on 2009-02-27
> **iaculallad said:**
> Does doing it from the terminal outputs the same error?

```
sudo shutdown -r now
```

Yep, gave it a try just then and same thing happens. I just get screen for my computer brand and it freezes. If I start 'puter manually with power button then I get that same screen for usually only 3-4 seconds before moving on to boot agent.

---

### Post by jwbrase on 2009-02-28
> **Lunx said:**
> Yep, gave it a try just then and same thing happens. I just get screen for my computer brand and it freezes. If I start 'puter manually with power button then I get that same screen for usually only 3-4 seconds before moving on to boot agent.

You mean the manufacturer's splash screen (Dell or E-machine or whatever)?

---

### Post by Lunx on 2009-03-01
> **jwbrase said:**
> You mean the manufacturer's splash screen (Dell or E-machine or whatever)?

Yep, that's the one, it's the first screen I get when I boot computer. If I select retart from the desktop it only gets to this screen and then hangs (forcing computer by holding power button is only way I can turn it off). Howevever if I select shutdown from desktop and then switch 'puter on manually, it boots normally, the computer manufacturers screen appears briefly, then moves on to boot agent screen and fires up as normal

---

### Post by jwbrase on 2009-03-01
Maybe something's wrong with the BIOS? I don't *think* it would be a problem with Ubuntu, 'cause at that first splash screen the OS hasn't loaded yet. Do you have any other OS's on the machine? If so, what happens when you restart from them? I'm thinking it would probably freeze from the other OS's as well.

---

