---
title: "Gaim Internet Messenger error"
date: 2007-04-17
forum: Desktop Effects &amp; Customization
---

### Post by Terryr100 on 2007-04-17
Hi as a complete newbie here's my question.
Having installed Gaim Internet Messenger It will not open, It tries,flashes and closes,
anyone any idea what's wrong? I get no real error message I'm just blocked from opening application. How do I uninstall and re-install?Add remove says I need to use Synaptic Packet manager but then I'm completely lost as I cannot find the application,
Thanks in advance,
Terry

---

### Post by SoggyCornflake on 2007-04-17
So how did you install it?

you could check to see if it's only got root permissions.  In a Console try:```
sudo gaim
```

If you didn't use apt-get or aptitude to install it, then it might be problemsome.  To install it from Ubuntu pacakages type :```
sudo apt-get install gaim
```

If it doesn't work after that you may need to tweak a lot of permissions.

---

