---
title: "Unknown commands go into the background"
date: 2009-05-03
forum: General Help
---

### Post by defaria on 2009-05-03
Why is it that the following happens:

```
$ mroe /etc/passwd

[1]+  Stopped                 mroe /etc/passwd
$ fg
mroe /etc/passwd
bash: mroe: command not found
$ 

```

How can I turn off this 'If the command is not known then put it in the background" option?

---

### Post by defaria on 2009-05-07
Can somebody please confirm that this is or is not a problem for them too? This is very annoying. I can't believe that this happens to everybody else but I have no idea of how it can be happening to me. It seems to me like this would need to be hooked into bash itself to cause it to "do something on unknown command". I didn't know that bash had such a facility...

---

### Post by ult007 on 2011-03-11
This is caused by command-not-found package. 
To disable it, either uninstall or comment it out in /etc/bash.bashrc.
Pretty annoying.

---

