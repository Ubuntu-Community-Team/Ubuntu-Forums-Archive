---
title: "Open Shutdown Dialog via shortcut key"
date: 2007-02-05
forum: Desktop Environments
---

### Post by FrancisA on 2007-02-05
Hello I'm looking for a the command (and this I want to bind to shortcut ideally to Alt-F4)
which opens the shutdown dialog as in windows xp.
I know the shutdown command, but this, I don't want (I don't want to shutdown at once).
I cannot find the name of this command.

Who can help me? :)

---

### Post by tszanon on 2007-02-05
When I install Ubuntu, it automatically binds the Power key to the shutdown dialog(Hibernate, suspend, restart, shut down....)

If you have the Power key on your keyboard, maybe you already have what you're looking for.

---

### Post by ardchoille42 on 2007-02-05
You can put the following command in a launcher, or make a custom keyboard shortcut:

```

/usr/bin/gnome-session-save --gui --kill

```

That is the command which is called when you click System -> Quit

---

### Post by FrancisA on 2007-02-05
> **tszanon said:**
> When I install Ubuntu, it automatically binds the Power key to the shutdown dialog(Hibernate, suspend, restart, shut down....)

If you have the Power key on your keyboard, maybe you already have what you're looking for.
Thank you, I didn't try out this until now.
But I think still, there must be a command to show that window.

---

### Post by FrancisA on 2007-02-05
> **ardchoille42 said:**
> You can put the following command in a launcher, or make a custom keyboard shortcut:

```

/usr/bin/gnome-session-save --gui --kill

```

That is the command which is called when you click System -> Quit

GREAT! I will try this out at evening, thank you very much!

---

### Post by FrancisA on 2007-02-06
Thanks, it works. The window is not in the foreground (it is covered by the window, which was before also in the foreground). But beside this, it is fine now.

---

