---
title: "read console output of tty7"
date: 2009-04-21
forum: General Help
---

### Post by Andreas1 on 2009-04-21
hi,
when i resume from suspend, i can see an error message for a second before x starts and replaces the console output. how can i access this output? if i do ctrl+alt+f1 it gets me to tty1, but the error message, as i understand, has been printed to tty7 where x server is running now (am i assuming correctly?)

---

### Post by ajmorris on 2009-04-22
> **Andreas1 said:**
> hi,
when i resume from suspend, i can see an error message for a second before x starts and replaces the console output. how can i access this output? if i do ctrl+alt+f1 it gets me to tty1, but the error message, as i understand, has been printed to tty7 where x server is running now (am i assuming correctly?)

hi there,
You could access the output in your 7th tty by killing X (i.e. a ```
pkill X
```)

However, all xorg messages/errors are sent to /var/log/Xorg.#.log where # is the number screen. By default, it will be /var/log/Xorg.0.log


AJ

---

