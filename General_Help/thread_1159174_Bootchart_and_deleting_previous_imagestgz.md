---
title: "Bootchart and deleting previous images/tgz"
date: 2009-05-14
forum: General Help
---

### Post by coldReactive on 2009-05-14
Is there a feature that makes it so that it deletes the previous image(s) and tgz(s) from the directory each time it runs?

---

### Post by baseface on 2009-05-14
have you read the man page?
 
you could write a script to do it for you.
 
```
#!/bin/bash
rm /path/to/whatever;
exec bootchart

```

---

### Post by coldReactive on 2009-05-14
> **baseface said:**
> have you read the man page?
 
you could write a script to do it for you.
 
```
#!/bin/bash
rm /path/to/whatever;
exec bootchart

```

And where do I put such a script?

---

### Post by baseface on 2009-05-14
i dont know how bootchart works. i dont even know what it is. but im gunna guess that you have to run it manually every time u want it to do whatever it does?
if thats the case, you wouldnt have to put the script anywhere in particular, just run the script.

---

### Post by coldReactive on 2009-05-14
Boot chart runs during the boot process, executing it during Ubuntu won't prove useful.

---

### Post by trpnblies7 on 2009-05-14
I don't know much about scripting, but I assume you could write a script that would delete all but the newest files in the bootchart folder upon loading Ubuntu. Then you could have this script run at startup so you wouldn't have to manually do it each time.

I would actually like to have something like this as well because I've been trying to figure out a way for bootchart to only keep the newest chart.

---

