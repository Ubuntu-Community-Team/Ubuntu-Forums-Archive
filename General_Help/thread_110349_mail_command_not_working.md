---
title: "mail command not working"
date: 2005-12-30
forum: General Help
---

### Post by cotn on 2005-12-30
Hi all, 

Because I did a full removal of postfix (for reinstallation), the mail command was accidently removed too. Stupid, I know :).

Can someone point me in right direction to get this back.

sudo apt-get install mail (just a guess) is not the solution I found out. 

thanks in advance.

---

### Post by cotn on 2005-12-30
Hmm, 

Okay just discoverd the problem myself: postfix also removes mailx.
So a reinstall of mailx was the solution.

---

