---
title: "Disable Windows Animation"
date: 2006-06-19
forum: Desktop Environments
---

### Post by karuptdata on 2006-06-19
Hello to all i am looking to disable the windows animation in GDM is this at all possible?? Thanks in Advance!

---

### Post by Ramses de Norre on 2006-06-19
In gnome you mean?
```
gconf-editor /apps/metacity/general
``` and check "reduced_resources"

---

### Post by karuptdata on 2006-06-19
yes sorry about that..and thank you it worked like a charm... :D =D>

---

### Post by darkultra on 2006-10-29
Wow this is an old workaround from 2004!

[I]You are absolutely right. The key is in apps -> metacity -> general. Too bad "reduced_resources" does not explain that it has anything to do with window animations.
Anyway, it certainly beats recompiling.[/I]
[http://gnomesupport.org/forums/viewtopic.php?t=5259](http://gnomesupport.org/forums/viewtopic.php?t=5259)


The option also disables "show window content while dragging and resizing" which I'd like to have enabled ](*,) 

I can't understand why its not easier to disable window animation as the animation is making me less productive. And its annoying too; ugly and jerky. Maybe only patient and balanced people use Gnome hehe

sorry for rant

---

