---
title: "failed log in after changing resolution"
date: 2010-03-31
forum: Desktop Environments
---

### Post by bl77122 on 2010-03-31
Hi,

I am new to Linux, but I managed to install Ubuntu 9.10 (the recent one) from the scratch using my old PC.  Ubuntu was very impressive until I failed to log in the gnome session.  It seems like I can't log in Unbuntu whenever I change resolution to a lower one than the default.  I still can log in Ubuntu by logging in the command line mode and typing 'startx'. 

I found a similar problem and resolutions in the following thread.

[http://ubuntuforums.org/showthread.php?t=1307810](http://ubuntuforums.org/showthread.php?t=1307810)

But, I don't understand what I need to do.

Is there any reading material that I (Windows guy) can read and try out to fix the problem by myself?

Thank you,

Bruce

---

### Post by dusdus on 2010-03-31
in the link you provided one solution might be, getting into the terminal and not type "startx", but instead:
```

/usr/bin/xrandr --output LVDS1 --off

```
and then:
```

/usr/bin/xrandr -s 1440x900 -r 60

```

(fill in your own resolution and refresh-rate)

He made a script of it and let it automatically run on boot.

Try if typing this manually helps, if not, go looking for some errormessages in /var/log/Xorg.0.log or /var/log/dmesg or... wherever in /var/log/ :)

---

### Post by bl77122 on 2010-03-31
> **dusdus said:**
> in the link you provided one solution might be, getting into the terminal and not type "startx", but instead:
```

/usr/bin/xrandr --output LVDS1 --off

```
and then:
```

/usr/bin/xrandr -s 1440x900 -r 60

```

(fill in your own resolution and refresh-rate)

He made a script of it and let it automatically run on boot.

Try if typing this manually helps, if not, go looking for some errormessages in /var/log/Xorg.0.log or /var/log/dmesg or... wherever in /var/log/ :)

Hi Dusdus,

I will try.  By the way, does it fix the problem permanently?
Can I log in Ubuntu normally after running these two commands?

Thank you,

Bruce

---

