---
title: "Script on Start Up."
date: 2009-12-13
forum: Desktop Environments
---

### Post by jv2112 on 2009-12-13
I put together a script to update packages, delete downloaded packages, fixed orphaned packages and display disk usage. I want it to run on boot up but I am stuck. I tried adding to "Start Up applications" (System->Preferences->Start Up Applications) nut no luck. 

It works fine running manually but I am at a loss to automate. 

Any Ideas ? ](*,)

---

### Post by govt_cheese on 2009-12-13
When you execute the command manually, do you have to use sudo? 
If so, after adding the script to the start-up apps, setup the script to execute without password. Use the command:

```
visudo

```

Add a line for your username and the script:

```
username ALL=(ALL) NOPASSWD:/path/to/script
```

---

### Post by falconindy on 2009-12-13
Just add it to /etc/rc.multi.

---

