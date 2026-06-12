---
title: "compiz fusion won't start [tried fglrx + XGL, 'radeon' + AIGLX]"
date: 2007-07-09
forum: Desktop Environments
---

### Post by SpanishFranks on 2007-07-09
Hi all, 
I have been using beryl succesfully with fglrx and XGL for a long while. I removed beryl and installed compiz fusion. After entering:
```
 compiz --replace
```

I get the error:
```
/usr/bin/compiz.real (core) - Error: Could not acquire compositing manager selection on screen 0 display ":1.0"
/usr/bin/compiz.real (core) - Fatal: No manageable screens found on display :1.0
```

I still get this error after using the open radeon driver with AIGLX. However this time direct rendering is enabled.

A strange quirk is after recieving these errors, if i then enter 'compiz --replace' again in the terminal, compiz starts albiet with a junk/black/artifacted wallpaper. I am using xfce and a mobility 9700

Any ideas?

---

### Post by SpanishFranks on 2007-07-09
FIXED

It turned out it was an xfce issue. For any others in the same boat heres the solution:

```
 sudo mousepad /etc/xdg/xfce4-session/xfce4-session.rc
```

Change
```
Client0_Command=xfwm4
``` to read ```
Client0_Command=compiz-manager
```

---

