---
title: "Why an activated root-account in Gutsy but not in Dapper?"
date: 2008-01-05
forum: Desktop Environments
---

### Post by Azyx on 2008-01-05
Hi when i first installde Ubuntu there were no root-account activated, and the reason was security. You should not activatet If you didn'nt need it. othewise you should use sudo.

There is not any i Dapper, but I saw just now that there are in Gutsy. I wounder why.

---

### Post by sumguy231 on 2008-01-05
There's no root password by default in Gutsy, at least with a normal desktop install. It's the same as it ever was.

---

### Post by Azyx on 2008-01-05
> **sumguy231 said:**
> There's no root password by default in Gutsy, at least with a normal desktop install. It's the same as it ever was.

If I go to System--> Administration --> Users and Groups I get at Users settings window with an user and root. According to that window the root has a login name and a home-dir, and if you look at property it also have an password.

but in dapper, there i only the user.

But i test now and it's not possible to log in as root, but It's little confusing. The root has no Previlegies activated in user and group settings..

---

### Post by mcduck on 2008-01-05
> **Azyx said:**
> If I go to System--> Administration --> Users and Groups I get at Users settings window with an user and root. According to that window the root has a login name and a home-dir, and if you look at property it also have an password.

but in dapper, there i only the user.

But i test now and it's not possible to log in as root, but It's little confusing. The root has no Previlegies activated in user and group settings..

It's just what you see in the Users and Groups that has changed. There has always been a root user in Ubuntu, there has to be one on a Linux system. And root also has to have home directory.

In the end everything is just like in previous versions, there is root user, but root has no password, and logging in as root is impossible.

BTW, it doesn't matter whatever the Users and Groups says about the privileges of root, as root always has rights to do _anything_ on a Linux machine.

---

