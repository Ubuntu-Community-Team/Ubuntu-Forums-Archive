---
title: "shutdown without asking for password"
date: 2005-08-31
forum: Desktop Environments
---

### Post by GOwin on 2005-08-31
When I shutdown from XFCE, i get asked for my password.

What do I configure so I can shutdown my computer without a password?

---

### Post by bored2k on 2005-08-31
> Passwordless logout for Xfce 4.2
```
sudo visudo
```
Add this:
```
your-username-here ALL = NOPASSWD: /usr/sbin/xfsm-shutdown-helper
```

("your-username-here" is the username) Most important is "ALL", which means 'all hosts' You may cut & paste that line into your sudoers file and it will work fine. Replace "your-username-here" with "ALL" if you want any user to be able to shutdown the machine.
That's it.

---

### Post by GOwin on 2005-08-31
Wow! that's fast.

thanks.

---

### Post by zeca_pedra on 2005-10-16
Had the same problem and I hoped this could solve it but for some reason, when I do ```
sudo visudo
``` I always get this:
```
 sudoers file: syntax error, line 24 <<<
sudo: parse error in /etc/sudoers near line 24

```

And now I have all the options in grey and can't reboot or shutdown

Now what shall I do? Did I destroy all my system? How? I can't believe on this!!!

Any ideas would be appreciated

---

