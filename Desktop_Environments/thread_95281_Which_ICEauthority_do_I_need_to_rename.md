---
title: "Which ICEauthority do I need to rename?"
date: 2005-11-26
forum: Desktop Environments
---

### Post by bailout on 2005-11-26
I can't start X and I think the problem is my ICEauthority file. I have searched the forums and see lots of posts about it but when I did a locate it showed one file in / and one in /home/. Which one do I need to delete/rename or do I need to do both?

thanks

---

### Post by GeneralZod on 2005-11-26
It should be /home/<username>/.ICEauthority, or ~/.ICEauthority for short :) You can either delete it, or chown it so that you own it e.g.

```

sudo chown <username> ~/.ICEauthority

```

---

### Post by bailout on 2005-11-26
Thanks for the reply. I renamed the file in /home/<uname> and x started fine.

---

