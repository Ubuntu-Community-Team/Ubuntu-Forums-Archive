---
title: "CTRL-ALT-DEL nas no effect in X"
date: 2007-07-13
forum: Desktop Environments
---

### Post by rashaba on 2007-07-13
The infamous CTRL-ALT-DEL has no effect in X. Is there any way in Ubuntu (7.04) to change this behaviour? I'd like to be able to issue a system-wide shutdown command with this key combination and I edited /etc/event.d/control-alt-delete to run the desired command.
But CTRL-ALT-DEL is only recognized on the console. Is this behaviour by design in Ubuntu? Please enlighten me.

---

### Post by bonzodog on 2007-07-13
Yes, i think this is the default, as the WM takes over the keyboard input and thus the console does not see it.

Your best bet might be to make a keyboard shortcut to the command in Gnome, or whatever window manager you run.

---

### Post by rashaba on 2007-07-14
Thanks for your quick reply.

---

