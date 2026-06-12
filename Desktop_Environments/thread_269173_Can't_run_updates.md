---
title: "Can't run updates"
date: 2006-10-01
forum: Desktop Environments
---

### Post by snakedog on 2006-10-01
I just installed Xubuntu last week.  Ran "sudo apt-get update" ok, then got nmap installed.  When I run Update Manager, it shows the updates I supposedly need, I click "Install Updates" and get a progress window saying it's examining the system, but nothing seems to happen.

Apparently I'm having issues with repository indexes.  Specifically these:

us.archive.ubuntu.com
archive.ubuntu.com
security.ubuntu.com

What happened?

---

### Post by Kateikyoushi on 2006-10-01
Try this

```
apt-get clean
apt-get update
```

---

