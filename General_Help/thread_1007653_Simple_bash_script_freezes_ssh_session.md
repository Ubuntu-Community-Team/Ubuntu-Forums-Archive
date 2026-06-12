---
title: "Simple bash script freezes ssh session"
date: 2008-12-10
forum: General Help
---

### Post by jonberling on 2008-12-10
Hello everyone,

I have a simple script that I run. It's the 'll' command, and this is it:

```
ls -l --color $*
```

It runs find when I am in front of the machine, but when I ssh in (using putty on Vista) it freezes the session. ctrl-c does nothing, but I can use ctrl-z to send it to the background.

Anyone know what's going on?

UPDATE:
If I type ```
ls -l --color
``` into the command line it works fine, its only when I put into a shell script. Its a very odd problem. 

I did some more experimenting, and I found a solution. I changed the script to:

```

#!/bin/bash
ls -l --color $*

```

Now it works fine. Go figure.

---

### Post by Dr Small on 2008-12-10
PuTTY can't handle color, perhaps?

---

### Post by reality1011 on 2008-12-10
works fine for me... putty can handle color...

---

