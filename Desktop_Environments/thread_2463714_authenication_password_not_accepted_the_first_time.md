---
title: "authenication password not accepted the first time."
date: 2021-06-16
forum: Desktop Environments
---

### Post by glenndavid077 on 2021-06-16
When logging into the desktop, my password is not accepted the first time, usually is accepted the second time. I always check what I typed when possible especially when typing the password. The problem also shows up on Gnome Terminal, I always have to type the root or system password more than once to get it to take. Many apps asks for the root password and they have the same problem. It is annoying, but not a critical problem. I have not checked out the internet to see if this is a common problem or one of a kind.

---

### Post by TheFu on 2021-06-18
I suspect the issue is that the keyboard takes a little longer to wake than the monitor does on your system.  Try typing 2 characters, then backspacing 2 times before entering the login password.

Any chance that a non-English input locale is used? Just asking. I suppose the GUI input and console input languages could have become divergent.

Ubuntu doesn't use a "root" password and desktop applications shouldn't ask for it - ever.  The only password used on 99% of stock Ubuntu systems might be the current userid's password to unlock sudo.  The length of time that sudo can be used without a password prompt can be configured. I don't know what the default time is - perhaps 5 minutes?  One of the first things I do on every new system installed, right after purging nano, is to change the sudo timeout value to be a little more convenient.

---

