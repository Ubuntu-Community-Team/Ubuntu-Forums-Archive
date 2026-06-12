---
title: "Prevent root login LXDM"
date: 2012-01-13
forum: Desktop Environments
---

### Post by alexkarro on 2012-01-13
I want to prevent root logging using the login screen (LXDM) so that I'm forced to login in to a normal user and then invoke su/sudo. 

I've looked in the configuration files of LXDM and I've found a blacklist user line but that doesn't work sadly.

Does anybody know a way of preventing root login using LXDM?

---

### Post by ankspo71 on 2012-01-17
Aren't you using *ubuntu?

All officially supported Ubuntu variants lock the root user account upon installation because it is a serious security risk to have enabled.

> 
"Every cracker trying to brute-force their way into your box will know it has an account named Root and will try that first. What they don't know is what the usernames of your other users are. Since the Root account password is locked, this attack becomes essentially meaningless, since there is no password to crack or guess in the first place." [https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

What you will need to do is delete the root user's password and lock the root user account. 

Open a terminal and paste the following:
```
sudo passwd -dl root
```

A reboot will be necessary for the changes to take effect.

---

