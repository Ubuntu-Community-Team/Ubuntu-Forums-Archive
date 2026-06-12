---
title: "Help setting up cyphesis"
date: 2009-10-21
forum: Gaming &amp; Leisure
---

### Post by wubifun on 2009-10-21
I am having some trouble setting up Cyphesis (a WorldForge server) but it won't work. I cannot set up the admin accounts, but I can create an account and play in an empty world with Sear and create an account in Ember but not actually play.

cypasswd -a admin results in:

 ```

New admin password: 
Retype admin password: 
2009-10-21 11:48:22 NOTICE DATABASE: row number 0 is out of range 0..-1
Segmentation fault

```

cypasswd:

```

2009-10-21 11:48:56 ERROR Error selecting row.
2009-10-21 11:48:56 ERROR DATABASE: ERROR:  relation "accounts" does not exist
Account admin does not yet exist

```

UPDATE: Ember is now working after a restart of X

Can anyone suggest a fix?

---

