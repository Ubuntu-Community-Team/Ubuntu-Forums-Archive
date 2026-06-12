---
title: "Can't install anything after creating a new user account"
date: 2009-06-14
forum: General Help
---

### Post by colau on 2009-06-14
Hi,
I created a new user account from System>Administration>User and Groups.
Logging into that account running this command
```

user1 is not in the sudoers file.  This incident will be reported.

```
What to do?

---

### Post by dcstar on 2009-06-14
> **colau said:**
> Hi,
I created a new user account from System>Administration>User and Groups.
Logging into that account running this command
```

user1 is not in the sudoers file.  This incident will be reported.

```
What to do?

User accounts do not have Administration rights by default and therefore cannot install/remove things.

---

### Post by colau on 2009-06-14
> **dcstar said:**
> User accounts do not have Administration rights by default and therefore cannot install/remove things.
Logging into the main user account,System>Administration>User and Group selecting the newly created user account checked the administration property and it is solved.

But now logging into the newly created user account when I click
System>Administration>User and Group I got a message.
```

The configuration could not be loaded.

```
Why is that?

---

### Post by colau on 2009-06-14
Adding administrative previleges [COLOR="Red"]rebooted[/COLOR] and it's solved.

---

