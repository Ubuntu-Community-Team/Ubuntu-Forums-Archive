---
title: "why is the full path needed to start the service"
date: 2009-05-08
forum: General Help
---

### Post by lieperik on 2009-05-08
I am rather new to Linux. What I don't understand is what is the difference between the two scenarios below:

**Scenario 1**
1 - Browser to the folder: /etc/init.d
2 - Hit enter
3 - Enter: sudo backuppc start
4 - Hit enter

Now I receive the error message: *command not found*

**Scenario 2**
1 - Enter: sudo /etc/init.d/backuppc start
2 - Hit enter

Now it works without error. What is the difference between the two scenarios? I used that if I first browse to the folder and use the backuppc start comment that it would start the service. Why is the full path required for doing this?

Many thanks,
Marcel

---

### Post by Johan! on 2009-05-08
Scenario 1 doesn't work because /etc/init.d/ is not in the PATH
sudo ./backuppc start should work.

./ makes sure that you start the script in the current folder.

---

### Post by dcstar on 2009-05-08
> **lieperik said:**
> I am rather new to Linux.
.......
Why is the full path required for doing this?


Because unlike DOS/Windows, Linux does **not** use the current directory to find executables - it only uses the PATH variable or explicit paths.

This is done for very good reasons, you can do a web search to find them.

---

