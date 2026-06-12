---
title: "Screenshot of login screen?"
date: 2006-07-02
forum: Desktop Environments
---

### Post by neonfiremanqtip on 2006-07-02
Is it possible to take a screenshot of the login screen in dapper 6.06?

thanks.

---

### Post by 23meg on 2006-07-02
You can use xnest to run a nested X session to accomplish this.

---

### Post by aysiu on 2006-07-02
To be more specific, you'll have to install the *xnest* package from the repositories: ```
sudo aptitude update
sudo aptitude install xnest
```

Then, use this command to run it: ```
gdmflexiserver --xnest
``` A new login screen will open inside of your current session.

---

### Post by ash211 on 2006-07-02
[QUOTE=aysiu]Then, use this command to run it: ```
gdmflexiserver --xnest
```[/QUOTE]

This command doesn't work with KDE (obviously, from the gdm).  Is there a KDE equivalent?

---

### Post by aysiu on 2006-07-02
I actually did that screenshot from KDE, but you're right--you would need GDM installed. I'm not sure what the KDM equivalent is. ```
kdmflexiserver --xnest
``` doesn't work.

---

### Post by neonfiremanqtip on 2006-07-03
Thanks to everyone that responded... that worked like a charm.

---

### Post by Ramses de Norre on 2006-07-03
I get this when I try to start a second X server:
```
**Cannot start new display**

The nested X server (Xnest) is not available, or GDM is badly configured.
Please install the Xnest package in order to use the nested login.
```

---

### Post by aysiu on 2006-07-03
What does that mean--GDM is badly configured? Can we assume you *do* have *xnest* installed?

---

### Post by Ramses de Norre on 2006-07-03
Yes, I installed it after reading this thread. Does it matter that I use fluxbox and not gnome? I do use gdm as display manager though.

---

### Post by aysiu on 2006-07-03
That may have something to do with it. Since we're using the command *gdmflexiserver*, I'm wondering if that invokes some library that's related to Gnome and not GDM directly...

---

### Post by Ramses de Norre on 2006-07-03
Ow and gnome is installed, so all libraries are here it's just not running.

---

### Post by aysiu on 2006-07-03
[Unfortunately, there don't seem to be a lot of people with this problem](http://www.google.com/search?num=100&hl=en&lr=lang_en&safe=off&q=%22The+nested+X+server+%28Xnest%29+is+not+available%22+or+GDM+is+badly+configured.&btnG=Search).

---

### Post by Ramses de Norre on 2006-07-03
[QUOTE=aysiu]Unfortunately, there don't seem to be a lot of people with this problem.[/QUOTE]
Not with a clear solution at least (could be me not understanding it), and there seem to be people who run it with fluxbox.

---

