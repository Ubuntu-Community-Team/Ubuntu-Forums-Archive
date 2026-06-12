---
title: "Uninstalling Boxee"
date: 2009-05-23
forum: General Help
---

### Post by pgohlke on 2009-05-23
ok right now i am running boxee on a dell mini 9. Something has gone wrong with it and i would like to reinstall, but i cant find out to to uninstall. sudo apt-get remove boxee does nothing it just says couldn't find package boxee, and it doesn't show up in synaptic or any other package manager. Please help!

---

### Post by KhurramM on 2009-05-23
use:

locate boxee

or

whereis boxee

or

dpkg -s boxee

it will tell u, hopefully.

Next use:

dpkg -P boxee

and install the latest update.

Hope this helps u.

---

### Post by lawtlm on 2009-08-24
I am also having trouble uninstalling Boxee.  When trying to uninstall I also got the message package not found.  I followed the next instructions and found Boxee but now don't know what to do to unintall it.
I am new to Ubuntu so I am sure I am missing a simple step.

---

### Post by simonsocial on 2010-01-24
Try...

sudo apt-get remove boxee


Worked for me.

---

### Post by JColeChanged on 2010-03-17
```

sudo apt-get remove boxee

```

Worked for me as well.

---

