---
title: "unset HISTSIZE .bashrc"
date: 2010-01-07
forum: Desktop Environments
---

### Post by ForgivenByJC on 2010-01-07
If I put in /etc/profile or ~/.bashrc```
export HISTSIZE=10000
export HISTFILESIZE=10000
```and reboot, then from gnome-terminal```
$: echo $HISTSIZE
10000
$: echo $HISTFILESIZE
10000
$: unset HISTSIZE
$: unset HISTFILESIZE
$: echo $HISTSIZE

$: echo $HISTFILESIZE

$:
```But if I change /etc/profile or ~/.bashrc to```
unset HISTSIZE
unset HISTFILESIZE
```they revert to 500.  How can I stop them from going to the default when unset in /etc/profile or ~/.bashrc?

---

### Post by SalahTr on 2010-01-08
> **ForgivenByJC said:**
> How can I stop them from going to the default when unset in /etc/profile or ~/.bashrc?
Why do you want that :?: if for disabling ***command history*** you could use :
```
set +o history
```

---

### Post by ForgivenByJC on 2010-01-13
I am trying to unlimit HISTSIZE and HISTFILESIZE.  Will unset not do this?

---

