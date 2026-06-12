---
title: "Dapper: where &quot;System Tools -&gt; New login&quot; gone?"
date: 2006-07-30
forum: Desktop Environments
---

### Post by qwen71n on 2006-07-30
Hi,

I am trying to play around with Fluxbox while continuing doing some work within a usual Gnome seccion. However, I found that in a freshly installed Dapper this option is simply gone! :-(  Does anybody know how can I open a new gdm login? I tried 

```

$ X :1

```

but this calls a new Gnome session, not gdm login. Any ideas?

Thanks!

---

### Post by ardchoille on 2006-07-30
What does this do:

```

startx -- :1

```
note the spaces.

---

### Post by qwen71n on 2006-07-30
> **ardchoille said:**
> What does this do:

```

startx -- :1

```
note the spaces.

this opens a new Gnome session. Anyway, just I found how to open a new gdm session: System -> Quit -> Switch user

Not too intuitive, eh?

---

