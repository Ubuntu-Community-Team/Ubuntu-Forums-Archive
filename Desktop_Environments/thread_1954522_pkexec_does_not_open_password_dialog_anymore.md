---
title: "pkexec does not open password dialog anymore"
date: 2012-04-08
forum: Desktop Environments
---

### Post by tuxolero on 2012-04-08
Hi there,

I am using xubuntu, but I am pretty sure that other variants are affected too.

My problem started with being unable to start synaptic from the menu.
So far, I have found out that synaptic is started with pkexec, the successor of gksu.

When I test starting
```
pkexec /usr/sbin/synaptic
```
in a terminal, it asks for the password in text mode.

According to the pkexec man page, there should be some authentication agent registered somewhere.

With another test 
```
pkexec --disable-internal-agent /usr/sbin/synaptic
```
in the terminal, it says it has not found any authentication agent.

So, the question is: where is the authentication agent registered ?

Thanks and Regards,

Markus

---

