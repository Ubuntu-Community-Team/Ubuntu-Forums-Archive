---
title: "acroread won't work"
date: 2005-11-23
forum: Desktop Environments
---

### Post by excelsior on 2005-11-23
I've installed the packages, but i got this error msg:

 acroread
shell-init: error retrieving current directory: getcwd: cannot access parent directories: No such file or directory
/usr/bin/acroread: line 12: /usr/lib/Acrobat5/bin/acroread: No such file or directory

when I look at the /usr/lib/Acrobat5/bin directory, i find acroread.sh instead of acroread. I tried sh acroread.sh and it doesn't work either (says it cannot find installation directory)

Help!

---

### Post by dcstar on 2005-11-23
I gave up on acroread long ago, the Evince reader seems more flexible (and it works.......)

---

### Post by sherlock-holmes on 2006-03-24
[QUOTE=excelsior]I've installed the packages, but i got this error msg:

 acroread
shell-init: error retrieving current directory: getcwd: cannot access parent directories: No such file or directory
/usr/bin/acroread: line 12: /usr/lib/Acrobat5/bin/acroread: No such file or directory

when I look at the /usr/lib/Acrobat5/bin directory, i find acroread.sh instead of acroread. I tried sh acroread.sh and it doesn't work either (says it cannot find installation directory)

Help![/QUOTE]
you might be in some other application directory than home . just run acroread from the home directory and see....

---

### Post by ekarni on 2006-03-24
Any idea what's with the "Acrobat5" in the directory?  Version 7 is current.  You did just grab the package using Synaptic, right?

---

