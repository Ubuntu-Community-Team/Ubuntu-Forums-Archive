---
title: "Does XMMS not work with Ubuntu w/ XGL/Compwiz?"
date: 2006-09-04
forum: Desktop Environments
---

### Post by zigx on 2006-09-04
I searched google for a bit but couldnt find anything.  Can anyone confirm if XMMS does not work when XGL is installed on Gnome?

When i use a session w/o xgl it loads up fine.  When i use a session WITH XGL it loads then closes instantly.

Any ideas on what might be wrong or how i can trouble shoot this baby?

thanks guys!:KS

---

### Post by bluevoodoo1 on 2006-09-04
> **zigx said:**
> ...how i can trouble shoot this baby?

Open it from a terminal and see what it says.

---

### Post by zigx on 2006-09-05
bluevoodoo1, thank you for suggesting that!  


When i ran it from a terminal i got the following:

> xmms
Gdk-ERROR **: BadMatch (invalid parameter attributes)
  serial 407 error_code 8 request_code 2 minor_code 0

I searched line 2 on google and found that there is a bug in XMMS with regards to 

XMMS set to 'Double Size' 

with      

Option "Composite" "Enable" in /etc/X11/xorg.conf .  

Composite is for making transparency, etc (XGL/Compiz use this) i think and apparently the bug has already been logged by a Gentoo user: [http://bugs.xmms.org/show_bug.cgi?id=1907](http://bugs.xmms.org/show_bug.cgi?id=1907)


Work around:
Load a NON xgl session and set XMMS to not use double size.  Load up ur xgl session and relaunch XMMS.  It works fine with double size off.

---

### Post by zigx on 2006-09-05
another workaround here: [http://bugs.xmms.org/show_bug.cgi?id=1907#c5](http://bugs.xmms.org/show_bug.cgi?id=1907#c5)

---

### Post by Dinerty on 2006-09-05
> **zigx said:**
> I searched google for a bit but couldnt find anything.  Can anyone confirm if XMMS does not work when XGL is installed on Gnome?

When i use a session w/o xgl it loads up fine.  When i use a session WITH XGL it loads then closes instantly.

Any ideas on what might be wrong or how i can trouble shoot this baby?

thanks guys!:KS

Mine does work, but loads pretty distorted, messed up graphics, loads fine in normal gnome though without xgl.

Does your load up with messed up graphics?

---

### Post by Pitxyoki on 2006-10-12
I was having exactly the same problem as you, but under aiglx/Compiz - from [here](http://gandalfn.wordpress.com/howto-compiz-aiglx-on-dapper/).
If you have a shortcut on a panel or a menu and use it to start xmms, you will find it very annoying to have to launch it from a terminal everytime... You can set this line in the launcher's "command" field (right-click -> Properties -> "Command"):
```
/bin/sh -c "XLIB_SKIP_ARGB_VISUALS=1 xmms %U"
```

It works. :)

---

