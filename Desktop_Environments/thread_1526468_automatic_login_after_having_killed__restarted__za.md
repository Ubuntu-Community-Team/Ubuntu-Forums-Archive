---
title: "automatic login after having killed / restarted / zapped the X server?"
date: 2010-07-08
forum: Desktop Environments
---

### Post by sall on 2010-07-08
Hi,

I'm setting up a mythTV frontend, so have set up automatic login in GDM, which works perfectly. I've also re-enabled the "kill X server" key combo (ctrl-alt-backspace), as other people here are used to that to restart it if everything goes pear-shaped.

However, the autologin isn't working properly after I kill the X server -- just sits at the login screen, and I have to manually log in.

Any idea how to fix that? Essentially, I never want to see the log in screen -- I want it to always log in as my generic MythTV user.

Not sure if it's any help, but here's my /etc/gdm/custom.conf:

```

[daemon]
AutomaticLoginEnable=true
AutomaticLogin=generic
TimedLoginEnable=false
TimedLogin=generic
TimedLoginDelay=1
DefaultSession=gnome
```

(I've also tried enabling the "TimedLoginEnable", and have tried delays of 0, 1, and 10 seconds. They don't seem to work, either.)

Thanks!

---

### Post by sall on 2010-07-13
No one? or, is there any more info I should provide, or should I be posting this elsewhere that anyone knows of?

---

### Post by sall on 2010-08-17
anyone?

---

### Post by nomiz on 2011-01-14
bump!

---

