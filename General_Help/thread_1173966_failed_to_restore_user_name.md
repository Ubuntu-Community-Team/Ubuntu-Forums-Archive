---
title: "failed to restore user name"
date: 2009-05-30
forum: General Help
---

### Post by nkarakos on 2009-05-30
Hi,
in a previous thread I described a problem I had with firefox
"http://ubuntuforums.org/showthread.php?t=1152756"
Sadly I had no reply and because it is a VERY annoying problem I tried to take drastic measures. So this is my new problem:

I deleted my initial ubuntu account called "nikolas" (the one that was created automatically during installation).
Then I tried to create a new account with the same name (nikolas) but I got an error message: User name "nikolas" already exists
How can it be since the account was deleted and I cannot login to it?

PS During all my actions I used the default ubuntu users-admin program.

---

### Post by geraldvillorente on 2009-05-30
follow this thread [http://ubuntuforums.org/showthread.php?t=358403](http://ubuntuforums.org/showthread.php?t=358403)

---

### Post by nkarakos on 2009-05-30
Thanks! It worked.
Well the problem is that when an account is deleted the _group_ that is associated to the account is not deleted as well.
I deleted the group "nikolas" from my system and success!

I thing that it is a bug of the program.

---

### Post by geraldvillorente on 2009-05-30
Ubuntu is still on its development process..so no wonder if we may encounter some problems...

---

