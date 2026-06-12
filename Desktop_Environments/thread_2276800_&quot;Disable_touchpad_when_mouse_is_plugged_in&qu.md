---
title: "&quot;Disable touchpad when mouse is plugged in&quot; not Working"
date: 2015-05-05
forum: Desktop Environments
---

### Post by gnagnibu on 2015-05-05
Hi everybody,

after upgradin to vivid, the  "Disable touchpad when mouse is plugged in" options isn't working anymore.
Could you confirm that?

Thanks

---

### Post by gnagnibu on 2015-05-05
My bad, the option is working.

You can ignore this thread

---

### Post by sudodus on 2015-05-05
Which method are you using to disable the touchpad? If you are using a GUI method, please describe it! If you are using a command line (in a terminal window), please post that command line!

What I know is that this command line works in Lubuntu 15.04, but I don't know the details about it in Kubuntu.

```
synclient touchpadoff=1
```

For more details, see ```
man synaptics
``` and look for [I][B]Option "TouchpadOff"

[/B]Edit:[/I] OK - I'm glad it works for you

---

