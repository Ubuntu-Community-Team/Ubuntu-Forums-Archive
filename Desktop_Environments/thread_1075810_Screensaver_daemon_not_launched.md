---
title: "Screensaver daemon not launched"
date: 2009-02-20
forum: Desktop Environments
---

### Post by jis on 2009-02-20
I installed Xubuntu 8.10 and noticed that screensaver daemon is not started in login.

/etc/xdg/xfce4/xinitrc script includes this:
```
# Launch xscreensaver (if available), but only as non-root user
if test $UID -gt 0 -a -z "$VNCSESSION"; then 
    if test x"`which xscreensaver 2>/dev/null`" != x""; then
        xscreensaver -no-splash &
    elif test x"`which gnome-screensaver 2>/dev/null`" != x""; then
        gnome-screensaver &
    fi
fi
```

I tried to run this as separate shell script (as #!/bin/sh) and got error: 
"test: 9: 0: unexpected operator"
If I take off outermost if clause, there is no error and gnome-screensaver gets started. What is wrong?

---

### Post by jis on 2009-02-21
The error occurs because $UID is an empty string in a Bourne shell script, but a number in a BASH script. Why is that? Does it work similarly in your *ubuntu 8.10 box?

---

### Post by jis on 2009-02-21
The xinitrc script includes this in the beginning so UID should not be the problem:
```
# fix broken $UID on some system...
if test "x$UID" = "x"; then
        if test -x /usr/xpg4/bin/id; then
                UID=`/usr/xpg4/bin/id -u`;
        else
                UID=`id -u`;
        fi
fi

```

---

### Post by jis on 2009-02-21
It seems that xinitrc is not run in startup for some reason.

---

### Post by jis on 2009-02-21
It seems that my Xubuntu 8.10 used some default session, which did not run xinitrc. I had to explicitly choose Xfce 4 session in GDM to have Xfce session properly launched, including screensaver daemon (to make xflock4 work).

I installed 8.10 using the Xubuntu desktop CD, retaining old /home partition from Xubuntu 7.10 (which did not start a screensaver daemon either).

---

