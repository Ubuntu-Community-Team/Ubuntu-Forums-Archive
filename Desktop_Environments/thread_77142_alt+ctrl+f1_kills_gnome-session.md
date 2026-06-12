---
title: "alt+ctrl+f1 kills gnome-session?"
date: 2005-10-16
forum: Desktop Environments
---

### Post by puccaso on 2005-10-16
hi people i'v just set up ubuntu for a diehard windows fan, and he loves it
however, whenever i switch to term/tty1 or any other tty for taht matter
it kills teh current gdm/gnome-session!! why does it do that
i'v never seen that before
how can we circumvent this feature?

---

### Post by kvidell on 2005-10-16
Hitting Alt+F7 and/or Ctrl+Alt+F7 does not return you to your X environment?
Ctrl+Alt+Bkspc has a habbit of killing it off without restarting it like it's supposed to... but F1->F6 should just be vterms.
- Kev

---

### Post by puccaso on 2005-10-16
i know it should take me to one of the vterms however it doesnt.
after i do a ctrlaltf1, and back to f7 - it makes me RE-login via gdm and loose everything i was doing before! i'm sure you can see how that is a problem,
how do i fix it?!?

---

### Post by yage on 2005-10-16
In a Terminal try ```
more /var/log/Xorg.0.log
``` and see if it prints out an error message there

---

### Post by puccaso on 2005-10-16
yep, did that - it doesnt tell me anything substantial! i'v spent 3 days trying to get his adsl pci card working and now he cant navigate between vterms,
what could be causing this!? any ideas people?

---

### Post by salmankhilji on 2007-11-30
I have the exact same problem.  I have a Sony VGN FS 550.  This machine uses the Intel video driver 915 chipset.  I have never seen this problem before in any versions of Ubuntu.  It appears only in Gutsy.

Basically, switching back and forth between different sessions using CTRL ALT Fx keys is not reliable.  It kills the session that you are trying to switch to making you lose everything that you were doing.

This happens 80% of the time.

Someone please help :-(

---

