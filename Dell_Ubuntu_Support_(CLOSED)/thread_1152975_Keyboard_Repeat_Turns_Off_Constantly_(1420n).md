---
title: "Keyboard Repeat Turns Off Constantly (1420n)"
date: 2009-05-08
forum: Dell Ubuntu Support (CLOSED)
---

### Post by aidave on 2009-05-08
Does anyone else have this problem?

The keyboard repeat is constantly turning itself off, although it shows as checked in the Keyboard Settings applet.  If I uncheck it, and check it again, the repeat comes back.  It will eventually turn itself off, however.

I was wondering if anyone knew of a way to enable keyboard repeat from the command line?
Then I could write a script to turn it on every minute or something.

cheers

---

### Post by aidave on 2009-05-08
I figured a way to enable it from command line:

```

gconftool-2 --set /desktop/gnome/peripherals/keyboard/repeat --type bool 1

```

---

