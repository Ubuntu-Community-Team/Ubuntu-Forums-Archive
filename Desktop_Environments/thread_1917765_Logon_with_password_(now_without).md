---
title: "Logon with password (now without)"
date: 2012-01-30
forum: Desktop Environments
---

### Post by advet on 2012-01-30
I set up my user account in 11.10 to logon without password (no password option). Before I had password. Now, when I click unlock icon to setup my password back, it says: Authentication is required to change user data.
Nothing works including my old password.
I want to logon with password. What can I do?

---

### Post by ruffEdgz on 2012-01-30
When performing the functionality of 'automatic login' from my Ubuntu 11.10 machine, I was able to login without a password and was able to unlock my account with my password.

If you go into a terminal and type the following code:
```

sudo -l

```
Type in your password, does it show with what permissions you have on the box? If it doesn't and it keeps asking for your password until it fails, then that means the password you think is on the machine isn't.

You might need to follow this guide on how to reset your password from a LiveCD if you need to reset your password:

[https://help.ubuntu.com/11.10/ubuntu-help/user-forgottenpassword.html](https://help.ubuntu.com/11.10/ubuntu-help/user-forgottenpassword.html)

---

