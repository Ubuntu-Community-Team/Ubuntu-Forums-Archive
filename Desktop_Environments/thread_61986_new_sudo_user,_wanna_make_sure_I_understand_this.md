---
title: "new sudo user, wanna make sure I understand this"
date: 2005-09-02
forum: Desktop Environments
---

### Post by railz68 on 2005-09-02
I want to add another user to the sudo list. What I'm doing is making a second account for myself. So, I'll have myself with two accounts, my wife and two kids.

I ask because I don't want the other users ending up with root access. Having read and looked over the Starter Guide, I've found how to do it. But I want to make sure I understand how it works before doing it.

  >  1. Read General Notes
   2. export EDITOR=gedit && sudo visudo
   3. Append the following line at the end of file
  "system_username ALL=(ALL) ALL"
   4. Save the edited file (sample)



So, when looking into this file, I see the last line is -
> 
# Members of the admin group may gain root privileges
%admin	ALL=(ALL) ALL

I think this means, anyone added to the "admin" Group will have sudo use. I hope it does not mean "ALL" users now have root access.

Am I reading this right ?.

---

### Post by bjweeks on 2005-09-03
Yes, you are correct.

---

