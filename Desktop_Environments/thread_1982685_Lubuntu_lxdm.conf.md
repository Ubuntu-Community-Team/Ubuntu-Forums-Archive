---
title: "Lubuntu lxdm.conf"
date: 2012-05-19
forum: Desktop Environments
---

### Post by Worp8d on 2012-05-19
Hi,

I've just upgrade to Lubuntu 12.04 and I'm having some trouble getting lxdm.conf to behave the way I want it to. I want numlock to be enabled on startup and so edited /etc/xdg/lubuntu/lxdm/lxdm.conf as per the [man page]("http://manpages.ubuntu.com/manpages/lucid/man1/lxdm.1.html"), i.e. uncomment and set to numlock=1, but no joy.

I also am trying to disable guest login on startup via the same file by setting user list control in the section of the file:

[userlist]
## if disable the user list control at greeter
disable=1

Neither option is working. The numlock control worked in 11.10, though I haven't tried disabling guest login before. Thanks in advance for any ideas.

---

### Post by JC Cheloven on 2012-05-19
Hi, 

In /etc/lxdm/default.conf put the value ```
numlock=1
```

As for your second question, I guess you can blacklist the guest user in this same file, or put ```
disable=1
``` but I never did it actually.

---

