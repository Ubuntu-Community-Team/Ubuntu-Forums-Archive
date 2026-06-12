---
title: "conky load issue in Gnome"
date: 2008-07-19
forum: Desktop Environments
---

### Post by Timtro on 2008-07-19
Hi All,

I'm running the latest hardy on Nvidia with restricted drivers. I'm using TwinView to handle my dual head setup with two wide-screen monitors.

My problem is that when I put conky in my 'sessions', it loads up smack dab in between my two monitors (the middle of my desktop, technically). In my conkyrc, I have

alignment center_bottom

but when I start conky normally (from a terminal), it knows enough that center means slightly left of center, on the RHS of my main monitor.

I believe that the problem is that conky is loading before whatever software it is that TwinView uses to decide proper desktop placement. I don't know much about TwinView, but I do recall that it relies on a software to ensure that programs don't load in between the screens. I've tried looking this up, but I can't find the link again.

I'd think that specifying conky's load order to 99 would fix the problem, but it appears that this functionality no longer exists in Gnome, despite what Gnome's 'help' documentation says.

Any help would be greatly appreciated.

Cheers,


Tim.

---

### Post by easybake on 2008-07-19
Use this sleep script to replace in your sessions. Get rid of brackets and input your path to your conky script.

```
#!/bin/bash

sleep 30 &&
conky -c ~[PATH TO CONKY SCRIPT];
```

---

### Post by Timtro on 2008-07-19
> **easybake said:**
> Use this sleep script to replace in your sessions. Get rid of brackets and input your path to your conky script.

```
#!/bin/bash

sleep 30 &&
conky -c ~[PATH TO CONKY SCRIPT];
```

Thank you, I appreciate your workaround, but that's not really an acceptable fix (even though it will likely work in the short term).

From what I've read, there is some controversy regarding gnome devs removing the 'order' functionality from the sessions menu. There must be some work around, since it is essential for the functionality of some software to load before others... compiz for example. I assume since people aren't flocking en mass to KDE that there is an acceptable solution

Thank you again. I sincerely hope I didn't come off as rude. I truly do appreciate your time and opinion.

Cheers,


Tim.

---

