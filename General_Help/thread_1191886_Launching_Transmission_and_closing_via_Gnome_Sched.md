---
title: "Launching Transmission and closing via Gnome Schedule"
date: 2009-06-19
forum: General Help
---

### Post by TRANQU111TY on 2009-06-19
Launching Transmission via Gnome Schedule is simple:

```
DISPLAY=:0.0 transmission
```

But what do I enter for another task to close it?

Thanks for reading

---

### Post by Agent ME on 2009-06-19
"killall transmission" should do the trick.

---

### Post by TRANQU111TY on 2009-06-19
> **Agent ME said:**
> "killall transmission" should do the trick.

Unfortunately the task "DISPLAY=:0.0 killall transmission" or just "killall transmission" doesn't work although it does work in the terminal.

---

