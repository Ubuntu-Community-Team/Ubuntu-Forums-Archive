---
title: "Log in as Root"
date: 2005-05-17
forum: Desktop Environments
---

### Post by YaAqoB on 2005-05-17
Hello. When I installed Ubuntu I can't remember if I was asked for a root password.
How do I log in as root? I have enabled it in the login manager.
Is there a default password or am I screwed?

Cheers

---

### Post by lepetitalbert on 2005-05-17
[QUOTE=YaAqoB]Hello. When I installed Ubuntu I can't remember if I was asked for a root password.
How do I log in as root? I have enabled it in the login manager.
Is there a default password or am I screwed?

Cheers[/QUOTE]

hello,

[http://www.ubuntulinux.org/support/documentation/faq/root](http://www.ubuntulinux.org/support/documentation/faq/root)

Have a nice day.

---

### Post by YaAqoB on 2005-05-17
Thank you very much for your help. :)

---

### Post by jonfr on 2005-05-18
I find this methoud to be dangerus for securty reasions. Since normal users shoud never have admin privileges to start with.

---

### Post by SNo0py on 2005-05-18
[QUOTE=jonfr]I find this methoud to be dangerus for securty reasions. Since normal users shoud never have admin privileges to start with.[/QUOTE]
Normal users don't have root privileges... they have to sudo to get them. And who is allowed to sudo can easily be controlled....

So this approach is even more secure, because root is not allowed to log in.

---

### Post by enrymco on 2005-05-18
You can do this command "sudo passwd root"    to set root password.
UIbuntu  use by default the user that you have created at installation.
or you can select in GUI interface the root terminal for doing command as root.

Best wishes 

Enrico

[QUOTE=YaAqoB]Hello. When I installed Ubuntu I can't remember if I was asked for a root password.
How do I log in as root? I have enabled it in the login manager.
Is there a default password or am I screwed?

Cheers[/QUOTE]

---

### Post by jonfr on 2005-05-18
[QUOTE=SNo0py]Normal users don't have root privileges... they have to sudo to get them. And who is allowed to sudo can easily be controlled....

So this approach is even more secure, because root is not allowed to log in.[/QUOTE]
sudo gives them root power, and that i find to be dangerus. I find it alot smarter setup to force specal root login then give the power to the first user in some form or an other.

In Ubuntu case, this securty hole comes in the form of sudo.

---

### Post by compmodder26 on 2005-05-18
[QUOTE=jonfr]sudo gives them root power, and that i find to be dangerus. I find it alot smarter setup to force specal root login then give the power to the first user in some form or an other.

In Ubuntu case, this securty hole comes in the form of sudo.[/QUOTE]

Sudo is only allowed to the first user.  The person who installed the operating system in the first place.  This person is granted super user access.  All other accounts that are subsequently created do not have this priviledge (unless they are granted access).

Even if we fail to convince you that it is more insecure than allowing a root account, you can always fix this yourself.  Just create a root account and then revoke sudo priviledges to the primary account.

---

### Post by SNo0py on 2005-05-19
[QUOTE=jonfr]sudo gives them root power, and that i find to be dangerus. I find it alot smarter setup to force specal root login then give the power to the first user in some form or an other.

In Ubuntu case, this securty hole comes in the form of sudo.[/QUOTE]
Not really - only the first user has sudo-access and the access to sudo can be controlled very easily. So only allowed users are able to use sudo...

---

