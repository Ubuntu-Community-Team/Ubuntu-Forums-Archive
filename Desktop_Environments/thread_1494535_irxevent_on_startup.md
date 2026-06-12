---
title: "irxevent on startup?"
date: 2010-05-27
forum: Desktop Environments
---

### Post by djstava on 2010-05-27
I install lirc and want to prgram irxevent start automatic when the system start

```
System->Preferences->Startup Applications
```

Add an item,but that not works every time,means sometimes cannot work.

---

### Post by djstava on 2010-05-31
When I login system as root,irxevent works well.:P

---

### Post by disabledaccount on 2010-06-01
> **djstava said:**
> ... but that not works every time,means sometimes cannot work....that's because you dont wait for lirc daemon to start. The simplest way to solve such problems (not only with lirc) is to write small script like that:
```
#!/bin/bash
while [ -z "$(pidof lircd)" ]; do
  sleep 1
done
irxevent ....<your xevents>
exit 0
```...then invoke it as startup application ;)
...and don't forget to give it execution permission.

---

