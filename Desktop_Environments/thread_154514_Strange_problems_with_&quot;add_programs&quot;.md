---
title: "Strange problems with &quot;add programs&quot;"
date: 2006-04-03
forum: Desktop Environments
---

### Post by Warlon on 2006-04-03
Why won't the add programs tool sometimes work? I tried installing kipina training log, but after pressing apply, it just flashed the download progressbar once on the screen and then disappeared. I tried it several times with the same results. With synaptic it installed fine.

I usually have these same problems with updates shown by the update-notifier, so I have to use apt-get manually to get the updates.

Some programs seem to install through "add programs" with no problems.

Any ideas what could be causing this?

---

### Post by aysiu on 2006-04-03
Has it always been this way?

Maybe try ```
sudo apt-get update
sudo apt-get install --reinstall gnome-app-install
```

---

### Post by Warlon on 2006-04-05
Still no luck. :/ Can't remember was it like this when I first installed. :-k

---

