---
title: "restart Kde desktop?"
date: 2007-11-13
forum: Desktop Environments
---

### Post by dragon2611 on 2007-11-13
Is there a command I could run to restart the KDE desktop (i.e kill it and restart) without taking down the whole of X

sometimes my desktop stops responding and I cannot interact with all my desktop icons.

Also sometimes the drives don't show up in "storage media" don't know if its related.

---

### Post by bodyglove on 2007-11-14
> **dragon2611 said:**
> Is there a command I could run to restart the KDE desktop (i.e kill it and restart) without taking down the whole of X

sometimes my desktop stops responding and I cannot interact with all my desktop icons.

Also sometimes the drives don't show up in "storage media" don't know if its related.

ctrl+alt+backspace?

---

### Post by dragon2611 on 2007-11-14
> **bodyglove said:**
> ctrl+alt+backspace?

Thanks but Ideally i wanted to take down kde desktop without the whole X session (and my running apps) going down, a ctrl + alt backspace would kill the whole x server

---

### Post by kuja on 2007-11-14
If you could get a konsole up it might be doable.  "killall kdesktop && sleep 5 && kdesktop" should work. 

Then again, if it's defunct, you'll probably need to get the process id and use kill -9 instead of killall.

For restarting the panel you can do the same thing with kicker

If you can't get a konsole up, if you can switch to a tty (ctrl + alt + f1-6)), a command like this might work:
killall kdesktop (or usiekill -9)
kdesktop -display :0.0 (or whichever display you are using .... that's the likely "default")

---

### Post by dragon2611 on 2007-11-14
> **kuja said:**
> If you could get a konsole up it might be doable.  "killall kdesktop && sleep 5 && kdesktop" should work. 

Then again, if it's defunct, you'll probably need to get the process id and use kill -9 instead of killall.

For restarting the panel you can do the same thing with kicker

I'll try that next time, its not the panel thats crashing sometimes the desktop I cannot click any icons or interact with it at all yet the panel, menu and apps are still responding :confused:

---

