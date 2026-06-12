---
title: "dpkg error"
date: 2017-01-17
forum: Debian
---

### Post by dan1965w on 2017-01-17
dpkg error: error creating new backup file "var/lib/dpkg/status-old" : permission denied

Can help me?
Thanks you

---

### Post by &amp;KyT$0P# on 2017-01-17
> **dan1965w said:**
> Can help me?
Not without more info.

What were you trying to do?

How exactly were you going about it?
Was it through a graphical package manager?  If so, which package manager?
Or was it from a Terminal command, if so what command?

---

### Post by Bashing-om on 2017-01-17
dan1965w; Hello;

What exact command are you running ?
Be aware that the /var directory is a system directory requiring admin authority (sudo) to access .

[INDENT][INDENT]all in the process
[/INDENT][/INDENT]

---

### Post by dan1965w on 2017-01-17
When i make apt-get update
In the end say "dpkj was interrupted, you must manually run 'dpkj --configure -a' to correct the problem. 
And when make that give the error

---

### Post by Bashing-om on 2017-01-17
dan1965w; OK then;

Show us the complete output of terminal commands:
```

sudo apt update
sudo apt upgrade
sudo apt -f install

```
Place these outputs between code tags to maintain the readability .
code tag tutorial:
[http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168](http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168)
Pending these returns we then take the package manger's advise "  'dpkg --configure -a' to correct the problem. " .

We then get to the cause of the issue.

[INDENT][INDENT]ain't nothing but a thing
[/INDENT][/INDENT]

---

### Post by dan1965w on 2017-01-17
# sudo apt update
fakeroot:FAKEROOTKEY  set to 51770
fakeroot:nested operacion not yet suported 
 
#sudo apt upgrade 

fakeroot:FAKEROOTKEY  set to 51770
fakeroot:nested operacion not yet suported 
 
#sudo apt -f install
fakeroot:FAKEROOTKEY  set to 51770
fakeroot:nested operacion not yet suported

---

### Post by Bashing-om on 2017-01-17
dan1965w; Yrk !

What are you doing ? Trying to compile dpkg from source ? This does not appear to be a standard linux install .

So, what is the install environment?
Do you know that you have internet connectivity ?

[INDENT][INDENT]backing up 10 yards here and
[INDENT][INDENT][INDENT]punting
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by dan1965w on 2017-01-17
Debian
Installed on android phone

---

### Post by howefield on 2017-01-17
Moved to "*Debian*"

---

### Post by Bashing-om on 2017-01-17
exit:
stage right -

as I know nothing of android devices.

---

### Post by dan1965w on 2017-01-17
Why?

---

### Post by QIII on 2017-01-17
Why as in "Why was this moved to Debian?"

Because you have Debian installed.

---

### Post by dan1965w on 2017-01-17
U  can help me or not?

---

### Post by ian-weisser on 2017-01-17
Apt won't work on fakeroot.
It only works on real root.
It may look the same to you, but the kernel knows the difference.

How did you get fakeroot?

---

