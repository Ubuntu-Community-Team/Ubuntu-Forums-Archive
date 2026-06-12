---
title: "[SOLVED] bash script help needed, very simple"
date: 2008-12-19
forum: General Help
---

### Post by sambita on 2008-12-19
Hello there, I am writing a script to unmount my WD Passport and i came across something i don't understand.

I have this lines in the script:
```

LOCATION=$(grep Passport /etc/mtab)
echo ${LOCATION:0:9}
```

and when i run it, it states the following error

> ./script.sh: 5: Bad substitution


However, if i write the lines in a terminal it does what i expect it to do(shows "/dev/sdb1")

Im sure this is something very basic, but i have no idea cause its my first time messing around with bash. 

Thanks in advance!

---

### Post by RHTopics on 2008-12-19
Add or change your first line in the script to be:

```
#!/bin/bash

```

If it was:

```
#!/bin/sh
```

It uses the "dash" shell instead of "bash" and it will generate the error message you received.

---

### Post by sambita on 2008-12-19
That did the trick, thanks!

---

