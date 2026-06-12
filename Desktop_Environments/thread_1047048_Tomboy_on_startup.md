---
title: "Tomboy on startup"
date: 2009-01-22
forum: Desktop Environments
---

### Post by alkamid on 2009-01-22
Hello,

A few months ago I setup Tomboy to start on startup (I added it in "system->preferences->sessions"). I wanted it to open in tray so I couldn't use the default command ("tomboy --search"). Instead, I typed just "tomboy" and everything worked fine: tomboy ran on startup in tray. A few weeks ago it changed: now it's not starting in tray and when I click "close" it closes instead of minimizing. I don't recall installing any update for Tomboy, but maybe there was one. 
Anyone sees a way to solve this? I want it to start in tray again (I don't want it to open its window at startup).

---

### Post by alkamid on 2009-01-22
bump

---

### Post by alkamid on 2009-01-23
Bump (:

---

### Post by boof1988 on 2009-01-23
> **alkamid said:**
> Bump (:

Please consider waiting ~24hours between bumps.

Kind Regards...

---

### Post by alkamid on 2009-02-01
Sorry for that. Now I think it's time to bump again.

---

### Post by alkamid on 2009-02-06
bump

---

### Post by MaraMax on 2009-04-09
Do u start it with --tray-icon option?

tomboy --tray-icon

---

### Post by alkamid on 2009-04-09
Yes, it's not working though. I partly solved it by just adding Tomboy to gnome panel and removing it from startup. I asked about it on Tomboy IRC channel and they said there's nothing to be done with that.

---

### Post by LordNibler on 2009-06-01
> **alkamid said:**
> Hello,

A few months ago I setup Tomboy to start on startup (I added it in "system->preferences->sessions"). I wanted it to open in tray so I couldn't use the default command ("tomboy --search"). Instead, I typed just "tomboy" and everything worked fine: tomboy ran on startup in tray. A few weeks ago it changed: now it's not starting in tray and when I click "close" it closes instead of minimizing. I don't recall installing any update for Tomboy, but maybe there was one. 
Anyone sees a way to solve this? I want it to start in tray again (I don't want it to open its window at startup).

Hello,

I had exactly the same problem. I found a workaround:

I wrote a script:
```
#!/bin/bash
sleep 25 && tomboy;
```
and set this script to start on startup (added it in "system->preferences->sessions")

Now tomboy starts minimized and it is minimizing when I click "close".

P.S. I'm new to linux and Ubuntu and I don't understand such tomboy behavior.

---

### Post by Viva on 2009-06-01
Right Click on the panel and add the tomboy applet.

---

