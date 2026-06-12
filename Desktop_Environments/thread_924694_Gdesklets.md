---
title: "Gdesklets"
date: 2008-09-19
forum: Desktop Environments
---

### Post by MaindotC on 2008-09-19
I'm trying to start Gdesklets and I'm getting the following output:
```

amd64@amd64-desktop:~/Desktop/awn-extras-applets-0.2.6$ gdesklets 
Starting gdesklets-daemon...
Connected to daemon in 423 milliseconds.

==========================================================[09/19/08-20:35:25]===
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
[---]   81 


amd64@amd64-desktop:~/Desktop/awn-extras-applets-0.2.6$ 

```

Why is this?  Thanks!

---

### Post by Shazaam on 2008-09-19
It looks like you are in this folder/directory when trying to start gdesklets....
```
amd64@amd64-desktop:~/Desktop/awn-extras-applets-0.2.6$
```
Enter cd again and it should get you back to where you want to be to start gdesklets...
```
amd64@amd64-desktop:
```

---

### Post by MaindotC on 2008-09-20
Not funny Shazaam.  Anyone want to offer some real help and not sarcasm?

---

### Post by MaindotC on 2008-09-21
I just went with Screenlets.  Nothing more satisfying than replacing the problem instead of understanding it and fixing it.

---

### Post by y-lee on 2008-09-21
Your gdesklet problem is a bug that has been reported to launchpad at least twice that i have found. I found one person who claimed that downgrading to python 2.4 (Ubuntu currently uses python 2.5) would fix the problem. But i honestly couldn't advise someone to do that as python 2.5 introduces some new language features and thus some python programs wrote for 2.5 might cease to work. I also found another user claiming desktop effects might account for this  gdesklet error. Since I can't reproduce this error I can't be sure of either of these suggestions, and btw i use gdesklets and have BOTH python 2.5 and python 2.4 installed (I program in python and want my code to be downward compatible with py2.4) but I don't use desktop effects.

---

### Post by Shazaam on 2008-09-23
> **strAlan said:**
> Not funny Shazaam.  Anyone want to offer some real help and not sarcasm?

No humor or sarcasm intended and I am sorry you took it that way.

---

### Post by MaindotC on 2008-09-23
Thank you for the apology.  No harm done.

---

