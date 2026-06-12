---
title: "Is this a bug?"
date: 2006-12-16
forum: Desktop Environments
---

### Post by tomplast on 2006-12-16
Hi everyone.

I don't know if this is a bug so I would like to see if we can clear this up together.

I have logged in as an administrator and I try to add a user through the GUI (works without problems), everything seems to work to this point. It's just that if I try to switch user and login as the newly created it just doesn't work :/. And when I try to switch back to the original account the newly created user isn't in the user administration GUI's list anymore.

Could someone tell me if this is a bug or lack of implementation thingy?

UPDATE: Possibly there could be something todo with an old existing group with the same name as the newly create user?

---

### Post by paparucino on 2006-12-16
Try to look in /etc/group-
You should see your user and the group which is connected to.

---

### Post by tomplast on 2006-12-16
> **paparucino said:**
> Try to look in /etc/group-
You should see your user and the group which is connected to.

I know how to get everything working (I feel at home with CLI) it's just that I wonder if this was a bug or something.

---

### Post by az on 2006-12-16
Sounds like a bug to me.  Is this Dapper of Edgy?  Have you looked in the bug reports to see if someone else has reported it?

What happens to the /etc/groups file when you use the GUI to add users?

Can you reproduce the bug?

---

### Post by tomplast on 2006-12-16
> **azz said:**
> Sounds like a bug to me.  Is this Dapper of Edgy?  Have you looked in the bug reports to see if someone else has reported it?

What happens to the /etc/groups file when you use the GUI to add users?

Can you reproduce the bug?

I'm running Edgy and I haven't searched that much yet for bugs like that. I will follow your good advice and (try to) reproduce the bug in the upcoming days.

---

### Post by wulfhound on 2007-03-10
> **tomplast said:**
> I'm running Edgy and I haven't searched that much yet for bugs like that. I will follow your good advice and (try to) reproduce the bug in the upcoming days.

I am running Edgy Xubuntu and this is happening to me. I even rebooted and the user is not there. So, in short, I can't add ANY new users to this computer.

Sandaili

---

