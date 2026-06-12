---
title: "Unable to add a user"
date: 2009-06-02
forum: General Help
---

### Post by tbirchall on 2009-06-02
I installed the netbook remix on an Acer Aspire One.  When I launch the Users/Groups app, the Add User button is inactive.  I also can't select the root user.  I had read on a forum that the first user automatically has administrative privledges but I don't appear to.  Can someone tell me what I'm doing wrong?

Thank you,

Tom

---

### Post by albinootje on 2009-06-02
> **tbirchall said:**
>  Can someone tell me what I'm doing wrong?


Did you click on the "unlock" button ? Or was that button greyed out ?

With the command "groups" (in a terminal) you can check whether your user is in the admin group. Is that the case ?

If not, boot in "recovery mode", choose "root prompt", and add your user in the admin group with the command :
```

adduser your_old_username admin

```

---

### Post by camper365 on 2009-06-02
What you need to do is press the unlock button.
The user's and groups allows you to run as a regular user so you can edit your user information, but you can't edit other users until you run it with root privileges.

---

### Post by tbirchall on 2009-06-02
Thank you!  You people ROCK!  It wasn't obvious to me that was what the Unlock button was for.  Now I can expose my wife to Linux...  By the by, it is great that the Linux community supports the newbies so much. 

-Tom

---

### Post by albinootje on 2009-06-03
> **tbirchall said:**
> Thank you!  You people ROCK!  It wasn't obvious to me that was what the Unlock button was for.  Now I can expose my wife to Linux...  By the by, it is great that the Linux community supports the newbies so much. 


Good that you have it working now :)

---

