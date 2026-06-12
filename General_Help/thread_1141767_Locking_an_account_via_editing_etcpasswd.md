---
title: "Locking an account via editing /etc/passwd"
date: 2009-04-28
forum: General Help
---

### Post by sylvester_0 on 2009-04-28
Hello - I was just over at CompTIA's site looking at the [Linux assessment]("http://certification.comptia.org/resources/practice_test/linux_samplequestions.aspx") and can't figure out this question:

```
A new employee having a problem with account login has the following entry in the /etc/passwd file:
user1:*:51:501:John Doe:/home/user1:/bin/bash

What is wrong with this entry in the /etc/passwd file?

A. The UID is not valid.
B. The account is locked. {CORRECT ANSWER}
C. The UID and GID must match.
D. Spaces are not permitted between the first and last name.
```

At first the UID stuck out to me because I thought UIDs below 100 were reserved for system use. I've googled and only came up with three ways of disabling an account via /etc/passwd:

1. Putting a + in front of their username.
2. Putting a ! in front of the * in the second field.
3. Changing their shell to /bin/nologin

---

### Post by kanikilu on 2009-04-28
I believe the asterisk (*) indicates an invalid password.

---

