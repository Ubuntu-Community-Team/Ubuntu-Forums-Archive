---
title: "I can't get the AT command to work"
date: 2009-03-03
forum: General Help
---

### Post by ShadowTek on 2009-03-03
I'm trying to use the AT command to read a command from a file which will start the VLC media player at a certain time, but I can't seem to get it to work.
> 
```

at -f file 23:00

```file:
```

vlc

```I can then use ATQ to confirm that the AT job has been scheduled, but nothing happens at the designated time. A followup ATQ confirms that the AT job has expired.

I also read in another thread that someone else solved their problem by removing the "bin" entry in "/etc/at.deny". I tried that, but it made no difference.

What am I doing wrong?

---

### Post by unutbu on 2009-03-03
Try putting this in file:
```
#!/bin/sh
DISPLAY=:0 vlc

```

---

### Post by atippett on 2009-03-03
> **unutbu said:**
> Try putting this in file:
```
#!/bin/sh
DISPLAY=:0 vlc

```


that might work.. I tried to do the same thing loading a xterm.  A email was sent to the postmaster email address for my box saying the following:

Warning: This program is an suid-root program or is being run by the root
+user.
The full text of the error or warning message cannot be safely formatted
in this environment. You may get a more descriptive message by running the
program as a non-root user or by removing the suid bit on the executable.
xterm Xt error: Can't open display: %s
xterm:  DISPLAY is not set

---

### Post by atippett on 2009-03-03
User was right.  Have to set display variable.  Guess at doesn't take the env variables of the user when the commands r scheduled.

---

### Post by ShadowTek on 2009-03-04
> **unutbu said:**
> Try putting this in file:
```
#!/bin/sh
DISPLAY=:0 vlc

```

That did it, thanks. I didn't know that the display had to be set.

Also, I replaced the "bin" entry in "/etc/at,deny", and it's still working fine.

---

