---
title: "make a &quot;guest&quot; account load automatically"
date: 2009-04-20
forum: General Help
---

### Post by bded on 2009-04-20
my account is an admin but there are others who need to use pc as well, how can i make it to be sorta like windows login (like with the diff users to pick from) as it is now they will have to know to type in guest to login but i can't always be nearby to explain.

---

### Post by aeiah on 2009-04-20
im not sure there's a simple way do it this exactly. you could of course just put a note on the pc saying what the guest login password is, or you could have the computer login to this guest user automatically.

---

### Post by bded on 2009-04-20
> **aeiah said:**
> im not sure there's a simple way do it this exactly. you could of course just put a note on the pc saying what the guest login password is, or you could have the computer login to this guest user automatically.

if it were to login to guest automatically could i switch to my account easily?

---

### Post by aeiah on 2009-04-20
just as easy as logging out and logging in as your other account. 

but for simple administrative tasks you could still use sudo. your password is the same as your root password for admin stuff, but it would be different for your guests - they (or you) would be typing in your root pass and not the guest pass for admin related things under their login. if they dont know it, they cant do any damage but you could easily change things without logging out.

automatic login is an option in system > administration > login window i think. and add users / users and groups / whatever is somwhere in that menu too.

---

