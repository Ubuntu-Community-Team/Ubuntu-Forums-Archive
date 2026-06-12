---
title: "how to disable process is running in gnome-terminal?"
date: 2009-04-27
forum: Desktop Environments
---

### Post by sles on 2009-04-27
Hello!

After upgrade to 9.04 when I want to close gnome-terminal is says something like this- "there is process inside, are shure?"
This is very annoying.
Is it possible to turn this off?

---

### Post by mcduck on 2009-04-27
Press Alt-F2 and run "gconf-editor" (or start it from a terminal). Then browse to apps/gnome-terminal/global and disable "confirm_window_close". That's it. :)

---

### Post by sles on 2009-04-29
thank you!

---

