---
title: "[SOLVED] How do I get list of recently installed packages?"
date: 2009-01-09
forum: General Help
---

### Post by jis on 2009-01-09
I remember that there is some command for it but what command?

---

### Post by adamlau on 2009-01-09
There are many commands to achieve that. Here is a simple GUI method: Synaptic > File > History.

---

### Post by Excedio on 2009-01-09
Or just open a terminal and type...

```
History
```

---

### Post by sdennie on 2009-01-09
Try:

```

sudo more /var/log/apt/term.log

```

Or

```

more /var/log/dpkg.log

```

---

### Post by adamlau on 2009-01-09
```
history
```

Will not show packages downloaded and installed through Synaptic. I like the workaround, however :) .

---

