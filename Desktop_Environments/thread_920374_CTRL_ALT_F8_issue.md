---
title: "CTRL ALT F8 issue"
date: 2008-09-15
forum: Desktop Environments
---

### Post by bbldox on 2008-09-15
Hi all

Pressing CTRL+ALT+F8 should send me to the new X-session but instead of this, the only thing I see in terminal is  "Running local boot scripts..." 
It looks like this session stuck.


8.04.1 Hardy Heron
CTRL+ALT+F1/F6 works as usual (send to tty1-tty6)
/etc/inittab doesn't exist
NVIDIA proprietary driver installed

---

### Post by Pro-reason on 2008-09-15
Yes, it has always done that for me on Ubuntu.  The next X-session is at tty9.

---

### Post by bbldox on 2008-09-16
CTRL+ALT+F9 shows black screen for me. A blinking cursor at the top-left corner.

Trying to xtail the whole /var/log I see almost nothing when I press "ctrl alt f8".

*** ./Xorg.0.log ***
(II) Open ACPI successful (/var/run/acpid.socket)
(II) NVIDIA(0): Setting mode "1440x900_60_0"

*** ./acpid ***
[Tue Sep 16 12:32:18 2008] client connected from 6404[0:0]
[Tue Sep 16 12:32:18 2008] 1 client rule loaded

*** ./Xorg.0.log ***
(II) Configured Mouse: ps2EnableDataReporting: succeeded


Any ideas?

---

### Post by mali2297 on 2008-09-16
> **bbldox said:**
> CTRL+ALT+F9 shows black screen for me. A blinking cursor at the top-left corner.

Trying to xtail the whole /var/log I see almost nothing when I press "ctrl alt f8".

*** ./Xorg.0.log ***
(II) Open ACPI successful (/var/run/acpid.socket)
(II) NVIDIA(0): Setting mode "1440x900_60_0"

*** ./acpid ***
[Tue Sep 16 12:32:18 2008] client connected from 6404[0:0]
[Tue Sep 16 12:32:18 2008] 1 client rule loaded

*** ./Xorg.0.log ***
(II) Configured Mouse: ps2EnableDataReporting: succeeded


Any ideas?

The relevant log file should be called **/var/log/Xorg.1.log**. 

Which command do you use to launch the second X session?
Try
```

startx -- :1

```

---

### Post by bbldox on 2008-09-17
> **mali2297 said:**
> The relevant log file should be called **/var/log/Xorg.1.log**. 

Which command do you use to launch the second X session?
Try
```

startx -- :1

```

Ok, I've tried ```
startx -- :1
``` on tty2 (CTRL+ALT+F2). I've seen the X screen (the black-grey one) and.. it disappears. 
Now I see only some strings from Xorg.1.log like this one:
```
expected keysym, got XF86KbdBrightnessUp, line 72 of pc
```

Anyway, I couldn't do anything on tty8..

---

### Post by mali2297 on 2008-09-17
> **bbldox said:**
> Ok, I've tried ```
startx -- :1
``` on tty2 (CTRL+ALT+F2). I've seen the X screen (the black-grey one) and.. it disappears. 
Now I see only some strings from Xorg.1.log like this one:
```
expected keysym, got XF86KbdBrightnessUp, line 72 of pc
```

Anyway, I couldn't do anything on tty8..

Use the command
```

egrep "WW|EE" /var/log/Xorg.1.log

```
to only list warnings and errors.

---

### Post by bbldox on 2008-09-18
> **mali2297 said:**
> Use the command
```

egrep "WW|EE" /var/log/Xorg.1.log

```
to only list warnings and errors.

Well, nothing new=) I did that check before.

```

(WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
(II) Loading extension MIT-SCREEN-SAVER
(WW) Option "XkbVariant" requires an string value
(WW) Configured Mouse: No Device specified, looking for one...

```

The same strings I have in /var/log/Xorg.0.log

---

### Post by youarefunny on 2010-11-11
When you start a new x server it is started on CTRL+ALT+F8 an up.

Try this:
1. Go to tty1 login and launch 'startx -- :1'
2.	Press CTRL+ALT+F8.

You should now be looking at your new X server.  Enjoy

---

