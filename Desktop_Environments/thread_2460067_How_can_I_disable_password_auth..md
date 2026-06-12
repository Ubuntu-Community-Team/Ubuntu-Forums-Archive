---
title: "How can I disable password auth. ?"
date: 2021-04-01
forum: Desktop Environments
---

### Post by jeresavolainen on 2021-04-01
Hi!

I'm getting annoyed by constant password auth. pop up windows. How can I disable this feature, I've edited the parameter # PasswordAuthentication to no in /etc/ssh/ssh_cofig file. This didn't help.

Thank you!

---

### Post by CelticWarrior on 2021-04-01
Welcome.

Perhaps if you don't use that security hole that is auto-login, such "problem" won't happen.

---

### Post by ajgreeny on 2021-04-01
Constant password auth. pop up windows; really?

What activities are you doing that keep asking for a password?  Normal everyday use of the computer will not need your password unless you are trying to make changes to system files or the OS itself, eg installing/uninstalling any software or similar.

It is very bad practice to totally disable the password needed for system changes and I will not tell you here how to do this, nor do I believe anyone else will do so. I think you need to get your system set up once and after that the password will not be needed for ordinary uses, only for those that need root permissions as you are making changes to the roof file system

With regard to your ssh comment, using ssh for connections will have nothing to do with the password request when carrying out other actions, and if you have edited ***PasswordAuthentication*** to ***no*** in the ssh config file it will only take effect if you remove the # from the start of the line.  If you do so, make sure you have set up the authorisation public/private keys or you will never be able to connect over ssh.
[https://help.ubuntu.com/community/SSH/OpenSSH/Keys](https://help.ubuntu.com/community/SSH/OpenSSH/Keys)

---

