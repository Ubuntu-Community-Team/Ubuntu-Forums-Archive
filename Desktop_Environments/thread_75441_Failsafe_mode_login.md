---
title: "Failsafe mode login"
date: 2005-10-13
forum: Desktop Environments
---

### Post by kLy on 2005-10-13
Hi

If I enter runlevel 1 (either through init 1, or through booting into failsafe), I get something like:

"Enter root password (or type Control+D to continue)"

And Ctrl+D just goes into runlevel 2 again.

Problem is, in Ubuntu, there ain't no root password since the root account is locked. This happened since I enabled the root account (needed to install one thing or other) and then disabled it again with "sudo passwd -l root".

Can anyone help?
Thanks

---

### Post by kLy on 2005-11-02
This is from the ubuntu wiki:

> 
Q: I won't be able to enter single-user mode!

A: The sulogin program in Ubuntu is patched to handle the default case of a locked root password.


Not so! I still get the "Enter root password for maintenance" prompt. Even after a "sudo passwd -l root".

/etc/inittab calls sulogin with:
~~:S:wait:/sbin/sulogin

According to the manual, an -e switch there would bypass the password if there isn't one. So did my inittab get changed by some app or something and it should have a -e? I don't think so. Can anyone help?

Can anyone who hasn't modified their root password give me their entry in /etc/shadow so that I can revert it back to that one to see if it helps? I'm out of ideas.

Thx

---

