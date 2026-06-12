---
title: "desktop compiz manager issue"
date: 2010-07-27
forum: Desktop Environments
---

### Post by Blackbirdman on 2010-07-27
Numpty that I am I was looking in compiz manager apps, config 'work around' and ticked the box to enable system x to play nicely with glx (?) and everything froze solid. 

Now, on lumpy reboot, various programs are open but stuck fast, nothing works. 

I have tried alt+print desktop+r+e+s+u+b to no avail I think I need to revert to metacity.

Any ideas please as it was all going so well.


Just found this:

Ctrl+Alt+F1   login
rm -rf -.gnome2 .gconf .gconfd .metacity
Ctrl+Alt+F7

I'll give it a try and edit if it works

Now that's a magic script, worked perfectly

---

### Post by stinkeye on 2010-07-28
You could try ```
gconftool-2 --recursive -unset /apps/compiz
```


If it's the entry in workarounds "Force synchronization between X and Glx" to unmark...
```
gconftool-2 --type bool --set /apps/compiz/plugins/workarounds/allscreens/options/force_glx_sync 0
```

Ohh, too late.All good.

---

### Post by Blackbirdman on 2010-07-28
Many thanks Stinkeye I will keep that script in storage for now as I am back up and running.

The script previously mentioned has already done the trick.

I am considering tattooing it on my arm or something.

best

---

