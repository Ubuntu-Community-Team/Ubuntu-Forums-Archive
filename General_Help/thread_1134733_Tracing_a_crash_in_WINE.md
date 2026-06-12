---
title: "Tracing a crash in WINE"
date: 2009-04-23
forum: General Help
---

### Post by Volt9000 on 2009-04-23
I have a program I've successfully installed with WINE. The problem is when I click a button in the GUI the program crashes. At least, I assume it crashes-- the program just disappears with no notification whatsoever. The program works fine in Windows.

Is there any log that's generated, or some way to trace this program to find out WHY it's crashing?

---

### Post by Tim Sharitt on 2009-04-23
Running from the terminal may give some clue.
```
wine /path/to/program
```

---

### Post by Volt9000 on 2009-04-25
That did the trick, thanks!

---

