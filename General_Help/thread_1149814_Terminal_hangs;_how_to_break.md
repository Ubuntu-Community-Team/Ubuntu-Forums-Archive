---
title: "Terminal hangs; how to break"
date: 2009-05-05
forum: General Help
---

### Post by steinaro on 2009-05-05
I am still somewhat new to terminal. Sometimes I enter a bad command into terminal and after pressing enter it hangs for a while and does nothing. How can I break the process or whatever is happening in the background without closing terminal and starting over again?

---

### Post by maybeway36 on 2009-05-05
Ctrl+C should do the trick.

---

### Post by evanrmurphy on 2009-05-05
Ctrl+C is how you do that. It terminates the current foreground process.

Happy shelling! :)

---

### Post by steinaro on 2009-05-05
Thanks!!

---

### Post by decoherence on 2009-05-05
If Ctrl C doesn't do it, try Ctrl D, then Ctrl \ (backslash) These key commands send various types of 'stop' signals to the current foreground program.

If none of them work, type Ctrl Z, then type

```

jobs
kill %1

```

Where "%1" is the number the jobs command reports as associated with your runaway command. For instance, it could be "kill %2" or "kill %3" but you'll probably find it's %1.

If that STILL doesn't work, do the same as above but instead of "kill %1" use

```

kill -9 %1

```

If THAT doesn't work, I'd love to see what you did to tie up the terminal so bad! :lolflag:

---

