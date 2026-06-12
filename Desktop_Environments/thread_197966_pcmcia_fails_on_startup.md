---
title: "pcmcia fails on startup"
date: 2006-06-16
forum: Desktop Environments
---

### Post by lakelovers on 2006-06-16
The pcmcia function "fails" on start up, but my wireless router works fine and I see no hindrance to the operation. I'm not familiar with pcmcia, but I guess it relates to a wireless operation, so should I be concerned or go with "if it ain't broke do fix it." philosophy?

---

### Post by Nobber on 2006-06-16
I get that too, and yet I'm running Ubuntu on a desktop machine. Quite why it thinks I need PCMCIA support, I don't know. In any case, if everything seems to work, I wouldn't worry about it.

---

### Post by lakelovers on 2006-06-17
Thanks, NObber. . . I'll not worry about it.

---

### Post by Anduu on 2006-06-17
From the description for PCMCIA in Synaptic

> PCMCIA Card Services for Linux
This package provides the PCMCIA card manager daemon that can respond
to card insertion and removal events, loading and unloading drivers
on demand. PCMCIA cards are commonly used in laptops to provide
expanded capabilities such as network connections, modems, increased
memory, etc.

So if your using a regular PC it is pretty much useless.

---

### Post by djibi on 2006-06-20
Hi,
I've got the same problem.
But with that problem, Xserver can't start.
So, I have to try to solve it with the shell.
Someone know which package(s) I have to remove? (or something else to solve it...)

thanks

---

### Post by Ramses de Norre on 2006-06-20
```
sudo aptitude install sysv-rc-conf && sudo sysv-rc-conf
```

Search the pcmcia service and disable it for all runlevels.

EDIT: and I'm afraid that this service can't really stop X from booting.. I guess you'll need to solve that problem otherwise.

---

### Post by lamego on 2006-07-09
Ops, wrong forum, sorry.

---

