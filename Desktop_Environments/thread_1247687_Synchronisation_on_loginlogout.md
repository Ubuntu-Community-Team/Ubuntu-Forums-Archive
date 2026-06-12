---
title: "Synchronisation on login/logout"
date: 2009-08-23
forum: Desktop Environments
---

### Post by rexcze on 2009-08-23
Hi, I have special question. We have many computers with ubuntu 8.10 and all users home directories are on remote raid mounted via nfs. But it doesnt have good performance, so Iam looking for another solution. I have been thinkink about this:

User will login and "something" take his login name and will connect to network storage and rsync(or just copy) whole home dir from network storage to local disk and after user logout it will save home directory to the server and then shuts down the computer. Does anyone have any ideas? The logoff(shuttin) part is easy, but how to get the right login name on signin? Thx :-)

---

