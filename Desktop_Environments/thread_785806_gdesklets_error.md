---
title: "gdesklets error"
date: 2008-05-07
forum: Desktop Environments
---

### Post by Mindless Automata on 2008-05-07
When I try to run gdesklets, I have a gray window pop up that eventually disappears.  Nothing happens.

When I run it through terminal:
```

$ Starting gdesklets-daemon...
Connected to daemon in 423 milliseconds.

==========================================================[05/07/08-15:41:23]===
=== Unhandled error! Something bad and unexpected happened. ===

[EXC]
in /usr/bin/gdesklets: line 393 <module>
in /usr/bin/gdesklets: line 268 parse_command
in /usr/bin/gdesklets: line 177 __open_profile
in /usr/bin/gdesklets: line 167 __client_daemon
in /usr/lib/gdesklets/main/client.py: line 208 set_remove_command
in /usr/lib/gdesklets/main/client.py: line 38 __send
in /usr/lib/gdesklets/utils/xdr.py: line 75 recv
[EXC]/usr/lib/gdesklets/utils/xdr.py

[---]   70     chunk = ""
[---]   71     while (True):
[---]   72         try:
[---]   73             length = ord(s.recv(1))
[---]   74         except:
[ERR]>  75             raise XDRError
[---]   76 
[---]   77         if (length): chunk += s.recv(length)
[---]   78 
[---]   79         flag = s.recv(1)
[---]   80         if (flag == _CONT): continue

```

I'm on Hardy AMD64.

---

### Post by Mindless Automata on 2008-05-08
Nobody?

---

### Post by iwallet on 2008-05-08
yea i got the same error... but im using screenlets now and it works great!

---

