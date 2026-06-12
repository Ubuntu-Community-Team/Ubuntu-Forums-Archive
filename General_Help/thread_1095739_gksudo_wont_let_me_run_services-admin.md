---
title: "gksudo wont let me run services-admin"
date: 2009-03-14
forum: General Help
---

### Post by bobdobbs on 2009-03-14
Hi all.

gksudo won't let me service-admin from the gnome panel.

Basically, I want to be able to use ssh-agent to manage my ssh keys, so that I can achieve passwordless logins to remote computers.

But, I want ssh-agent to be run when I start an X session, so that I don't have to give my private key passphrase every time I open a shell.

I expect that if start ssh-agent on startup, I should be asked for my dsa passphrase when I try to login to an X session.

I managed to get this working on one ubuntu desktop, by adding ssh-agent via the service-admin applet.

However, on another computer, running Ibis, when I go to System -> Administration -> Services,

I am first asked for my password, which is accepted. Then, I get an error message that says:
```

Failed to run services-admin as user root.

The underlying authorization mechanism (sudo) does not allow you to run this program. Contact the system administrator.

```


How can I gain access to this part of the gnome panel?

Otherwise, is there another way to ensure that ssh-agent can manage keys across a login session on 8.10 ?

Thanks

---

