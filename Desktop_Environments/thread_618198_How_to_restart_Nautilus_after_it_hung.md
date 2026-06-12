---
title: "How to restart Nautilus after it hung?"
date: 2007-11-20
forum: Desktop Environments
---

### Post by mindhaq on 2007-11-20
Hello,

sometimes Nautilus seems to hang after waking up from Hibernate. The window is then greyed out and not responding at all. When I try to close it, a dialog is offering a forced quit (kill). Window closes, but I cannot open any new nautilus windows thereafter.

I tried clicking on the places in app menu, entering nautilus on shell (no output at all, nothing happens) and even killing a running nautilus thread. After killing, a new one seems to be started at once, but still no windows.

I looked in the syslogs, but I found no errors there.

When I run nautilus as root in the same session, it works.

So how can I properly restart nautilus without logging out or restarting the whole computer?

---

### Post by stani on 2008-01-30
Did you try:
```
$nautilus -q
```
This normally restarts nautilus.

---

### Post by yurtos on 2008-05-18
that did not work for me but this helped:

```
sudo killall nautilus
```

---

