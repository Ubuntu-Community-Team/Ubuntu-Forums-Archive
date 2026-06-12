---
title: "caching problem with permissions"
date: 2006-10-15
forum: Desktop Environments
---

### Post by fm1234 on 2006-10-15
Hi,

I was logged in in gnome as user "faky". In one terminal session, while in "sudo su mode" I created a group "family" and added a few users to it. In another terminal, I used the command "groups" but it doesn't show the "family" group in the list. However, if I enter the command "groups faky" then it does indeed show the complete group list.

As a consequence, I had permissions problems to create files/directories in the folder of another group user. Logging off gnome was enough to fix the problem.

So, there is a cache inconsistency problem (in gnome/terminal) going on, although I'm surprised since I thought permissions where handled at kernel level.

In any case, the fact that "groups" and "groups faky" give different results points clearly to a bug (at least a design one).

Should I report this problem somewhere else?

---

