---
title: "Suspend within GDM, but not Gnome?"
date: 2006-06-11
forum: Desktop Environments
---

### Post by malius on 2006-06-11
For the past couple weeks, I have been searching for a way to suspend my desktop to ram.  After searching the forums, I have yet to find a definitive answer.

Today I noticed that GDM has a suspend option.  After selecting this option, my machine went to sleep like I would expect it to.

Now my question is, how do I enable this functionality within the Gnome desktop?  I do not wish to log out every time I wish to suspend my machine!

I've tried playing around with the power management settings within Gnome, but I still cannot see the option to suspend within the **Quit** Dialog.

Any help would greatly be appreciated!

---

### Post by malius on 2006-06-15
If no one knows how to enable the suspend icon within the **quite** dialog, can someone tell be what script is called during a suspend action?

---

### Post by malius on 2006-06-15
Update...

I believe that I have tracked down the correct suspend script:

```
**gksudo [COLOR="RoyalBlue"]pmi action suspend force[/COLOR]**
```

The questions I have now are:
[LIST=1]
[*]How do I enable the suspend icon within the exit dialog?
[*]How do I run the above command as a normal user?
[/LIST]

---

