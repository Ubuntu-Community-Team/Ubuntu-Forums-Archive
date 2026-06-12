---
title: "Login screen loops"
date: 2006-09-12
forum: Desktop Environments
---

### Post by EchoRevamped on 2006-09-12
The bootup is fine, except for "/etc/init.d/mysql[4408]: Error: partition with /var/lib/mysql is too full!"  It then boots to the regular login screen.  After I try to login, the screen goes black and shortly after it reverts to the same login screen.  I can login fine using the terminal, but the kde login is my problem.  Any personal experience with this problem.  I need some help quick.

---

### Post by dbd on 2006-09-13
Is the partition full? This command will show you how much free space you have on each partition:
df -h

If  /var/lib/mysql is on the root partition and that partition is full (ie you don't have a separate var partition) then you can probably free some space with this command:
sudo apt-get clean
(that will remove from the downloads of the package files that were used when you install things, for more info see "man apt-get").

---

