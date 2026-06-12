---
title: "How do I switch window manager?"
date: 2009-03-31
forum: Desktop Environments
---

### Post by Hetor on 2009-03-31
Well, I want to try out another window manager. I've installed it, but when I try to run it, terminal repports an error:

```
E: awesome: xerrorstart:103: another window manager is already running.
```

How do I disable the default manager?

---

### Post by Simian Man on 2009-03-31
If awesome supports the --replace options, this should work:
```

awseome --replace

```

If not, you can kill your current WM and launch a new one in one command.  If you are using Xfce, your WM is called xfwm4 so:
```

killall xfwm4 && awesome

```

HTH

---

### Post by Locutus_of_Borg on 2009-03-31
If you use the GDM login screen, you can choose your session from there

if you use a text login, you can change your ~/.xinitrc file to exec awesome instead of whatever you are currently using, then startx will launch an awesome session

---

### Post by Simian Man on 2009-03-31
> **Locutus_of_Borg said:**
> If you use the GDM login screen, you can choose your session from there

if you use a text login, you can change your ~/.xinitrc file to exec awesome instead of whatever you are currently using, then startx will launch an awesome session

This is the way to go if you want to replace your whole Xfce desktop with awesome.  If you just want to replace the window manager component, my instructions are a way to do it.

---

