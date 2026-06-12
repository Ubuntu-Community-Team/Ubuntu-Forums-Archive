---
title: "sudo remembers password forever"
date: 2005-11-08
forum: Desktop Environments
---

### Post by DrBair on 2005-11-08
Just as the title says, sudo remembers the password forever!

My sudoers file is still at the default, no nopasswd option was added.  
I tried 'sudo -K' and 'sudo -k' with no success.
This has been going on for several days and survived multiple reboots. 
I also tried reinstalling sudo with no sucess. 

Other than that, sudo is working fine.  Its just a bit troubling to me...


Thanks for any input!:smile:

---

### Post by linbetwin on 2005-11-08
Have you tried "exit"? I don't think this is it. It's just a suggestion.

---

### Post by DrBair on 2005-11-09
Nope, thats not the issue.  Thanks for the reply though.


TTT :smile:

---

### Post by 23meg on 2005-11-09
Try this: type "sudo visudo" and add this to the end:

```
Defaults:ALL timestamp_timeout=0
```

---

### Post by DrBair on 2005-11-09
Still no go... 

Does anyone know of any files that sudo uses for keeping track of stuff? Maybe something is wrong with them in the permissions department.

---

### Post by 23meg on 2005-11-09
Did you modify any of your user settings? Try creating a new user and logging in with it and see if the problem persists.

---

### Post by DrBair on 2005-11-09
I added another user account and it was not effected by this problem.  

I then started hunting around some more, starting in /etc/group.  My 2 previous user accounts were in the sudo group and the new one was not.  All 3 could access sudo so I tried pulling the other 2 names out of the sudo group and everyone was happy again!

Does anyone else have people listed in their sudo group? I have a feeling that automatix did it, that seems to be when trouble struck.  Either that or when I started mucking with stuff though the gnome user admin tool. 

Thanks a bunch 23meg, I feel much better now!

---

### Post by jimbob on 2005-11-09
I installed using Automatix and there is no one in my sudo group.

---

### Post by 23meg on 2005-11-09
You're welcome, DrBair. And there seems to be noone in my sudo group.

---

