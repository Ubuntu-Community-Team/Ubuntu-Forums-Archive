---
title: "[SOLVED] Help -- how do I set up a launcher to start a terminal, change dir, and run"
date: 2007-12-19
forum: Desktop Environments
---

### Post by gilf on 2007-12-19
I currently have to open a terminal, change to a directory, and run a script there to start a particular application.

I would like to automate this from a launcher icon that could be clicked on the desktop.

Is there a way to open a terminal and then cd to a folder, then run a script in a launcher?

I was able to do this in Kubuntu, but now have switched to Ubuntu and can't find a way to do it (so far)

Thanks!

---

### Post by Whiffle on 2007-12-20
Under application type, theres some entry for terminal application, and then in the command line you could put:

```

/path/to/script

```

---

### Post by aidanr on 2007-12-20
```
xterm -hold -e "cd /path/to/script && ./script"
```

---

### Post by gilf on 2007-12-20
> **Whiffle said:**
> Under application type, theres some entry for terminal application, and then in the command line you could put:

```

/path/to/script

```

Whiffle, thanks for trying, but I had already tried that. While it tries to execute the script, the terminal is not cd'ed to the script directory, which is essential

> 
Code:

xterm -hold -e "cd /path/to/script && ./script"



aidanr thanks -- this one  for some reason failed once with a Java out of memory error from the application (CollabCAD) before it could open fully

Then when tried later it worked. So I assume it was actually a memory problem, and your command did the trick!.

Thank you kindly!

---

