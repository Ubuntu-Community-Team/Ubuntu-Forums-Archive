---
title: "remove ssh server"
date: 2009-01-30
forum: General Help
---

### Post by lex1 on 2009-01-30
if i remove the open-ssh-server from my system as people keep trying to get in will that solve the problem?

lex1:popcorn:

---

### Post by hyper_ch on 2009-01-30
depends on what the problem is.

---

### Post by neur0 on 2009-01-30
Sacred rule of security #46:
"If you don't need it, remove it"

But if you do need it, secure it (move it to a different port, use keys instead of passwords, disable root login...)

---

### Post by Mud.Knee.Havoc on 2009-01-30
Here's some advice if you want to use ssh, but want to avoid security problems.

You can also use fail2ban or denyhosts to stop people from trying to get in without authorization. Changing the port to something non-standard will have the same effect. (do both of these)

This will explain more about setting up ssh, which helps to understand how to make it more secure:
[https://help.ubuntu.com/community/SSHHowto](https://help.ubuntu.com/community/SSHHowto)

And this is a great list of ways to harden ssh security:
[https://help.ubuntu.com/community/AdvancedOpenSSH](https://help.ubuntu.com/community/AdvancedOpenSSH)

---

