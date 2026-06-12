---
title: "Gnome only works in failsafe mode"
date: 2007-05-03
forum: Desktop Environments
---

### Post by CeNoBiTa on 2007-05-03
Since a couple of days i'm having trouble with the gnome startup. It only starts correctly when in failsafe.

I've found this in the **.xsession-errors** file:

```

** (nautilus:5661): WARNING **: Can not caclulate _NET_NUMBER_OF_DESKTOPS

** (nautilus:5661): WARNING **: Can not calculate _NET_NUMBER_OF_DESKTOPS

** (nautilus:5661): WARNING **: Can not get _NET_WORKAREA

** (nautilus:5661): WARNING **: Can not determine workarea, guessing at layout

```

Can anybody help?

Thanks in advance!!

See ya.

---

### Post by Omegatron on 2007-05-15
I have the same exact problem.

Try renaming ~/.gnome2/session to ~/.gnome2/session-old

It doesn't fix it for me, but it did for other people.

---

