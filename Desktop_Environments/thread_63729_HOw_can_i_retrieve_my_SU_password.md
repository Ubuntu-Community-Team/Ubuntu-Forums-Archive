---
title: "HOw can i retrieve my SU password?"
date: 2005-09-08
forum: Desktop Environments
---

### Post by Lancelot on 2005-09-08
Thanks for the Ubuntu, software for humanity..
Coz even i'm far away country they send me a free software..thanks again,

But now this is my problem, how can retrieve my su password?
I forgot my password...Thanks..


-Lancelot

---

### Post by f1dave on 2005-09-08
Take a look at [www.ubuntuguide.org](www.ubuntuguide.org)

You'll see that ubuntu uses sudo instead of su to give the user root priveleges. Thus you don't need to worry about your root password.

---

### Post by Divan Santana on 2005-09-09
Hello, 

[http://ubuntuguide.org](http://ubuntuguide.org) tell's you what you need to know.

Basicly type:

sudo "and the command here"

eg...

sudo reboot

Password is your normal users password that you logged in with.(Thats if your user belongs to "sudo" group) - it will by default if it was first user created.

Divan

---

### Post by daller on 2005-09-09
What about:

sudo passwd

???

---

### Post by Takis on 2005-09-09
[QUOTE=daller]What about:

sudo passwd

???[/QUOTE]
That will set the password, not retrieve it. It's nearly impossible to retrieve passwords, for slightly obvious reasons. You shouldn't need to set the root password (in theory), anyway.

---

### Post by digitalmouse on 2005-09-10
[https://wiki.ubuntu.com//RootSudo](https://wiki.ubuntu.com//RootSudo) is also a good reference.

---

