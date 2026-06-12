---
title: "Locked Out"
date: 2009-05-06
forum: General Help
---

### Post by Ritun on 2009-05-06
Hello!

I have a virtual server running Ubuntu. I was notified that SSH was rejecting new connections(not even showing the login prompt before rejecting).

I have searched Google for solutions, but most yield solutions revolving around hosts.allow and hosts.deny. I have checked both files and that does not appear to be the issue.

Does anyone know what else may be causing this issue? Do I need to provide further information?

Thanks for the response!

---

### Post by kanikilu on 2009-05-07
Can you explain your setup further? You say it's a "virtual server", are you using VMWare or VirtualBox?

[This blog]("http://mydebian.blogdns.org/?p=148") explains how to do it with VirtualBox, but if you are using VMWare, I'm sure there is similar information out there on how to do it...

---

### Post by wirelessmonkey on 2009-05-07
Have you installed openssh-server, and if so is it running?
```
 ps aux | grep sshd
```

---

