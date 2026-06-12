---
title: "Quitting X Shortcut Disabled"
date: 2009-06-12
forum: General Help
---

### Post by Bubblebeard on 2009-06-12
Hi all,

Hitting Ctrl-Alt-Backspace used to quit X, but no longer does so.  I was messing around with keyboard shortcuts so probably disabled it by accident.  How would I re-enable it?

Thanks!

---

### Post by x33a on 2009-06-12
The shortcut combo has been disabled in jaunty.

to enable it:
```
sudo aptitude install dontzap
```

then
```
dontzap --disable
```

---

### Post by jenkinbr on 2009-06-12
> **x33a said:**
> The shortcut combo has been disabled in jaunty.

to enable it:
```
sudo aptitude install dontzap
```

then
```
sudo dontzap --disable
```

fixed it for you - you need to run that last command as sudo.

---

### Post by x33a on 2009-06-13
> **jenkinbr said:**
> fixed it for you - you need to run that last command as sudo.

thanks, i have only used it once after installing jaunty :popcorn:

---

### Post by Bubblebeard on 2009-06-13
Ok, Thanks!

---

