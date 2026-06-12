---
title: "How to get my password for my login"
date: 2007-06-15
forum: Desktop Environments
---

### Post by saikilaya on 2007-06-15
Can anyone help in recovering the password for my login other than root login. And I could not even log into root login.

---

### Post by gaiterin on 2007-06-15
Hi. In Ubuntu 7.04:
Maybe?... when the computer boot: Press Esc, and select with root acount (I don't remember if is "recovery mode").

---

### Post by mcduck on 2007-06-16
Boot into recovery mode and then run 'passwd username' (using your real username of course.) and then you can set new password. After that 'reboot' will restart the computer.

(And before anybody complains how unsecure the recovery mode is, if anybody gets physical access to your computer the security is already gone. Any live-CD will give full access to your files, removing BIOS passwords is a piece of cake and even encrypted files take just longer to access.. Anyway, it's possible to configure Grub to ask for password when accessing recovery mode if it makes you feel better.)

edit: about logging in as root, no, you are not even supposed to be able to do that. Not even if you have enabled the root account for some reason. If you want, you can enable logging in to desktop as root but why would you? Running desktop as root is one of the easiest ways to get rid of all security Linux has..

---

