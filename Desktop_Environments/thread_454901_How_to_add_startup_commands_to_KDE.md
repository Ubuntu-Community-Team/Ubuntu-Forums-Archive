---
title: "How to add startup commands to KDE?"
date: 2007-05-26
forum: Desktop Environments
---

### Post by loathsome on 2007-05-26
In GOME it's under "system &#8594; sessions" or something like that.

How do I add for example '/ram/myscript.sh' to start up with KDE, and KDE only?

Thanks!

---

### Post by pbw on 2007-05-26
Place (or symlink to) your script in ~/.kde/Autostart.

-- pbw

---

### Post by loathsome on 2007-05-26
Hi, thanks a lot :)

*edit:* nvm

---

### Post by loathsome on 2007-05-26
I just tried adding a bash script to ~/.kde/Autostart, and it didn't seem to work.
Yes, it's executable

When I manually launch it via konsole it works flawlessly. What did I do wrong?

**EDIT**: It works when I e.g create a symbolic link to /usr/bin/gaim, but not when I try to launch my shell script that looks like this: ```
#!/bin/bash
kde-window-decorator
compiz --replace
```

why ? ..

---

