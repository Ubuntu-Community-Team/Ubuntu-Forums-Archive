---
title: "&quot;Can't open display&quot; when starting xclock on ubuntu 8.04 root shell"
date: 2009-10-07
forum: Desktop Environments
---

### Post by tsanchung on 2009-10-07
kubuntu does not have a root account.
"gvim", "sudo gvim", "xclock" and "sudo xclock" are all running ok on a non-root shell on konsole.
$ gvim
$ sudo gvim /etc/fstab
[sudo] password for ts:

$ xclock
$ sudo xclock
[sudo] password for ts:

However, starting xclock or gvim on root shell on konsole has the "Can't open display" error appears.
# DISPLAY=localhost:0.0
# xclock
Error: Can't open display: localhost:0.0
# gvim /etc/fstab
E233: cannot open display
Press ENTER or type command to continue

# DISPLAY=:0.0
# xclock
Invalid MIT-MAGIC-COOKIE-1 keyError: Can't open display: :0.0
# DISPLAY=:0
# xclock
Invalid MIT-MAGIC-COOKIE-1 keyError: Can't open display: :0

---

