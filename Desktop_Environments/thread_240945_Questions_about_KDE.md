---
title: "Questions about KDE"
date: 2006-08-21
forum: Desktop Environments
---

### Post by PathSpace on 2006-08-21
I have not tried KDE since 2003, and am curious about trying it out briefly again.  What I am wondering is how it will interact with my (perfectly working) AIGLX/Compiz installation.  Will it mess it up in any way?

Also, can I install KDE Compiz packages alongside my GNOME Compiz packages, or must I give up having Compiz in GNOME to have it in KDE? 

Thanks in advance for any answers.

---

### Post by steve.horsley on 2007-11-01
Bump. 

I'd like to know this too.

---

### Post by wieman01 on 2007-11-01
I tried Compiz on KDE a while ago and I have to say it does not work too well together. I would rather refrain from using it. KDE 4 promises to have similar effects and eye-candy, so I would wait for the final release in December or so.

---

### Post by Whiffle on 2007-11-01
Works fine for me.  Emerald is a little buggy (randomly dies), but kde-window-decorator seems to be okay.

---

### Post by Zorael on 2007-11-01
KDE is awesome.

Your Compiz installation will likely work in KDE too, but unless you use a flat-file configuration backend (preferences in the settings manager), your settings may not transfer.

KDE Window Decorator is buggy for many - it won't even start for me after loading Compiz - but Emerald works okay. It crashes every now and then, but if you create a script to keep it running, it's less of an issue.

```
#!/bin/bash

while true; do emerald --replace; sleep 1; done &
```
(name it emerald.start, so when you want to close emerald you can just do 'killall emerald.start')

All in all, it's obvious less effort has been made to integrate Compiz with Kubuntu (it's not installed by default). As far as I understand things, the KDE developers are moving in a direction where they write their own desktop effects rather than use Compiz. Once you do set it up, however, I'd say it works fine.

---

### Post by wieman01 on 2007-11-01
> **Whiffle said:**
> Works fine for me.  Emerald is a little buggy (randomly dies), but kde-window-decorator seems to be okay.
Could you post instructions here? That'd be terrific.

What version of Ubuntu are you on? Kubuntu Gutsy by chance?

---

