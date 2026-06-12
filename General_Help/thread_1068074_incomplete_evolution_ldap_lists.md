---
title: "incomplete evolution ldap lists"
date: 2009-02-12
forum: General Help
---

### Post by garyprosser on 2009-02-12
I have evolution working with an ldap server based addressbook EXCEPT that lists do not always get expanded completely. 

A search directly against the ldap directory for cn=faculty@[our domain] with required attribute 'member' yields 1 entry with 17 members.

Meanwhile a search within evolution contacts for 'faculty' yields 1 contact which expands to 13 members.

Another search within evo (smt@[our domain]) correctly finds 1 contact with 4 members.

It seems the ldap directory entries are correctly configured but evolution has some kind of faulty ldap search result expansion.

Anyone found this ? Or have suggestions to fix ?

---

### Post by jonobr on 2009-02-12
SOunds like an old bug, by searching launchpad

[https://bugs.launchpad.net/ubuntu/+source/evolution/+bug/70026](https://bugs.launchpad.net/ubuntu/+source/evolution/+bug/70026)

---

### Post by garyprosser on 2009-02-15
> **jonobr said:**
> SOunds like an old bug, by searching launchpad

[https://bugs.launchpad.net/ubuntu/+source/evolution/+bug/70026](https://bugs.launchpad.net/ubuntu/+source/evolution/+bug/70026)

Maybe - but previous reports do not refer to lists and I get DO get individual contact details. Seems to me like a different issue to previous reports. Any advice on how to take this further with the bug reporting process ?

---

### Post by garyprosser on 2009-02-19
I found the reason for the incomplete expansion - one member of the faculty@ list had an ldap record lacking a mail attribute. It appears that the expansion of the list within Evolution ceased on reaching that 'misconfigured ?' member.

---

### Post by dcstar on 2009-02-19
> **garyprosser said:**
> I found the reason for the incomplete expansion - one member of the faculty@ list had an ldap record lacking a mail attribute. It appears that the expansion of the list within Evolution ceased on reaching that 'misconfigured ?' member.

Then that is the sort of thing you should file in a bug report so it gets addressed.

---

