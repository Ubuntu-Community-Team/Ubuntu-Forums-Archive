---
title: "User Self Registration &amp; Automatic Account Creation"
date: 2009-05-29
forum: General Help
---

### Post by rtobyr on 2009-05-29
Has anybody ever seen those places where you can get a free Unix shell account ([http://freeshell.org/](http://freeshell.org/) for example)? When you telnet or ssh in, you can register for a new account, and one is then automatically created. I want to do that, but I can't figure out how. I can't find any packages that seem to have that functionality. Any pointers?

---

### Post by kidders on 2009-05-30
Hi there,

Creating new accounts is fairly trivial ... you can do it with **useradd**. The biggest issue is that however you work it, something that normally shouldn't is going to have to act with root privileges in order to make the necessary system modifications, which present a security issue.

One possibility might be...
[LIST]
[*]Create a simple registration process with a captcha, email adddress verification or some other sort of intermediate step to keep bots out.
[*]Write a script that runs "sudo useradd ..." and whatever else you need. Have your registration process execute it at the end.
[*]Grant your web server passwordless access to the commands it needs with **visudo** (the dangerous bit). Be sure the username is properly escaped.
[/LIST]

I hope that helps.

---

