---
title: "Compiz troubles on 11.10"
date: 2011-11-30
forum: Desktop Environments
---

### Post by breakphreak on 2011-11-30
Installed Compiz configuration manager and enabled some options (such as wobbly windows, desktop cube etc). The wobbly worked, but after enabling the other one (I think it was desktop-<something>, but not desktop wall) - the window frames disappeared, the alt-tab stopped to work.

Upon the next re-login the only menu I see is of the file manager. Can't execute any other application (the wobbly still works).

The question is: what can I do to make it back to "normal"? Any configuration files I need to tweak? Any other way to launch the compiz configuration manager so I'll be able to disable the most of the things?

If I need to provide any kind of environment-related information - just ask.

Appreciate!

---

### Post by nothingspecial on 2011-11-30
Hi,

Press Ctrl-Alt-F1 to get to tty

Login then type 

```
unity --reset
```

That will hopefully get you back to normal.

---

### Post by r_mano on 2011-11-30
If alt-F2 works, you can launch the compiz configuration manager by typing 
ccsm (or /usr/bin/ccsm) at the prompt...

---

### Post by breakphreak on 2011-11-30
voila! 'reset' worked! thanks a lot :)

---

