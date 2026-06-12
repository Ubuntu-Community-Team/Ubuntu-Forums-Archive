---
title: "Update-Manager crashes X Desktop"
date: 2006-06-01
forum: Desktop Environments
---

### Post by daverab on 2006-06-01
I've had this issue since 6.06 Flight 6 after I toyed with the two expose-like tools.

When the Update-manager notification icon is up on the top panel and I attempt to run Update-manager, it will load, download the updates, then wait for input. Before I can even move the mouse to the window or anything, X crashes, and I find myself back at the login screen.

I had no luck getting help with this back with Dapper Beta. I have figured out it's somewhat related to the update-manager notification thing. When that wasn't active/running and nagging for updates being available, I was able to open Update-manager and use it without issue.

Any suggestions?

---

### Post by zeroconf on 2006-06-01
Try to use apt-get at console:
 1) sudo apt-get update
 2) sudo apt-get dist-upgrade

First step will upgrade package descriptions from repositories and second step will perform full system update. It will upgrade all programs you have installed.

---

### Post by daverab on 2006-06-30
I can still use that, I didn't try to fix it that way. I ended up just installing Dapper fresh again due to some other quirky issues I was having.

---

