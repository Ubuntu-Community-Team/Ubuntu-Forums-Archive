---
title: "Can't open display: :0.0"
date: 2006-06-15
forum: Desktop Environments
---

### Post by RikBlankestijn on 2006-06-15
Hi, i've trouble starting new programs at some point. Every time I come home from work I can't open new programs anymore because I get the following message:

```

rik@hanz ~ $ xterm
xterm Xt error: Can't open display: :0.0

rik@hanz ~ $ epiphany
cannot open display: (null)
Run 'epiphany --help' to see a full list of available command line options.

```

I can open a new window when a browser for example is already opened, I do Ctrl-n and a new window appears.

At first I thought maybe it's my screensaver, but I disabled it but the problem remains. Hopefully you can help me, suggest me something to try! thanks in advance!

---

### Post by Laestrygo on 2006-06-15
You need to change the DISPLAY variable

```
export DISPLAY=:0.0
```

---

### Post by RikBlankestijn on 2006-06-17
The problem is that is can not open display: :0.0 so it's already set to :0.0 that's whats so strange. I was thinking maybe there is a limit for opening displays on :0.0 and perhaps I reached the limit because of a process opening many displays?? I'm not sure. Can I see somehow how many displays there are already in use?

---

### Post by RikBlankestijn on 2006-06-19
anyone?

---

### Post by RikBlankestijn on 2006-06-22
Also, when this problem occurs I have to restart gnome. In the Logout menu the  "Shutdown" and "Restart" buttons are gone. I have to choose logout to return to GDM and then there is a whole different theme instead of the default theme. Hopefully someone can diagnose the problem?

---

### Post by scxtt on 2006-06-22
[QUOTE=RikBlankestijn]. . . Every time I come home from work I can't open new programs anymore . . .[/QUOTE]do you use your computer when you're @ work? ... or is it that it works fine before work, then you're gone for a while and when you come home it doesn't work (no usage when you're @ work)?

---

### Post by RikBlankestijn on 2006-06-23
[QUOTE=scxtt] ... or is it that it works fine before work, then you're gone for a while and when you come home it doesn't work (no usage when you're @ work)?[/QUOTE]

Exactly. Every day it's the same, I'm away from home for approximately 
 11 hours, but my girlfriend is at home 2 hours earlier and see also noticed the problem.

---

