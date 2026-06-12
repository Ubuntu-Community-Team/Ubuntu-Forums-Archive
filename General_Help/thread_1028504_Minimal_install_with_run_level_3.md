---
title: "Minimal install with run level 3"
date: 2009-01-02
forum: General Help
---

### Post by balloooza on 2009-01-02
I have noticed on  all the installs I do of Ubuntu, there is no way to boot into runlevel three, and no way to keep the gnome from installing (or the other desktops)
I was wanting to do a minimal install of ubuntu with text, and then run a small wm, like fvwm2.
is there an option in the alternate install disk to go without a desktop the FIRST time, because I do not want it starting into a desktop.

thanks, i wont be here for an hour or two,

---

### Post by cariboo on 2009-01-02
At the menu screen of the alternative install, type:

```
cli
```

This will install a minimal sytem to the command line. From there you can install what you want.

An alternative is to download the [mini.iso]("http://help.ubuntu.com/community/Installation/MinimalCD"), and do a net install to the command line.

Jim

---

### Post by balloooza on 2009-01-02
Thank you, those are booth good ways, I think I will try the alternate install.

---

### Post by dcstar on 2009-01-02
> **balloooza said:**
> I have noticed on  all the installs I do of Ubuntu, there is no way to boot into runlevel three, and no way to keep the gnome from installing (or the other desktops)
I was wanting to do a minimal install of ubuntu with text, and then run a small wm, like fvwm2.
is there an option in the alternate install disk to go without a desktop the FIRST time, because I do not want it starting into a desktop.


Simply remove the GDM start-up link from /etc/rc2.d and it won't then start.

---

