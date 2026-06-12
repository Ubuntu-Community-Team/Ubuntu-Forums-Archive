---
title: "sudoers list"
date: 2009-01-23
forum: General Help
---

### Post by theozzlives on 2009-01-23
I've got a lady and her son staying with me, and are using one of my old computers. I thought I gave the lady TRUE administrative rights when I setup the user, but on administrative tasks it says her name is not in the sudoers list.

  I want her to be able to decide what software goes on (no limewire, etc.), and keep track of her sons home folder (make sure he's staying out of trouble on my network).

  So anyhow what's the sudoers list and how do I add her?

---

### Post by drs305 on 2009-01-23
Sudoers is a special file that is a bit tricky to edit. An easier way is to go to System > Administration > Users & Groups. Unlock with your password, then highlight her name, select Properties > User Privileges and add her to "Administer the system". That will put her in the "admin" group and allow her to use "sudo".

---

### Post by gettinoriginal on 2009-01-23
System, Administration, users/groups, highlight her name, unlock needs your password, then priveledges and check what she can do with her password ie: "administer system"

---

### Post by albinootje on 2009-01-23
> **theozzlives said:**
> So anyhow what's the sudoers list and how do I add her?

Make sure her name is in the admin group, and have her logged out, and log in again after doing so :
```

sudo adduser her_user_name admin

```
(Yes, adduser can be used like this to add users to groups)

Easiest and fastest ;-)

---

### Post by theozzlives on 2009-01-23
I'm pretty sure I gave her rights to administer the system, didn't check the admin group though... I'll check when I get a chance. Don't the system automagically do that when you specify administrator in user setup?

or can I check remotely?

---

### Post by drs305 on 2009-01-23
> **theozzlives said:**
> or can I check remotely?

If you can access the machine, you can run:
```

groups *her.username*

```

The return should include the group *admin* if she has those rights.

---

### Post by albinootje on 2009-01-23
> **theozzlives said:**
> I'm pretty sure I gave her rights to administer the system, didn't check the admin group though... I'll check when I get a chance. Don't the system automagically do that when you specify administrator in user setup? 

I just tried this on my Ubuntu Hardy setup.
Added a new user via the -> System -> Administration -> Users&Groups
Did choose "Administrator" instead of "Desktop User", and the user was in group admin after that, as it should be.

Weird that it didn't work for you right away.

The "adduser her_username admin" command should show something like "use jane_doe is already in the admin group" if she was in the admin group already.

---

### Post by theozzlives on 2009-01-30
I finally got a chance to check, her name is checked in the admin group but not in her own group. Would that do it?

---

### Post by albinootje on 2009-01-30
> **theozzlives said:**
> I finally got a chance to check, her name is checked in the admin group but not in her own group. Would that do it?

Not in her own group ? That's weird :(
Add her username to her own group (same as username), and see whether that helps.
And can you post the output of :
```

lsb_release -a
sudo cat /etc/sudoers 

```

---

