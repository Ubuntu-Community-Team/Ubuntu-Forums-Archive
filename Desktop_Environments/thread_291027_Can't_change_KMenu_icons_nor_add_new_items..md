---
title: "Can't change KMenu icons nor add new items."
date: 2006-11-01
forum: Desktop Environments
---

### Post by Roque on 2006-11-01
In a fresh Dapper installation, icon changes in KMenu are not saved. If I add a new application to the menu, let's say KWrite, the new item appears as a blank line. Modifying the entry attributes in the right panel does nothing. This kind of change is not saved either. 

But I CAN add folders to the menu, move items from one folder to another. These changes DO get saved. 

I appreciate any help. Thanks in advance.

---

### Post by aysiu on 2006-11-02
Try this: ```
sudo chown -R roque:roque /home/roque/.kde
```

---

### Post by Roque on 2006-11-02
Thanks, but it didn't work. All files in kde where owned by myself already. I browsed the forums: some people having similar problems could solve them with your trick. Mine seems to be something different.

---

### Post by aysiu on 2006-11-02
Can you create a new test user and see if that new user has the same problem?

---

### Post by Roque on 2006-11-02
That's a good idea: the test user's KMenu works OK.

---

### Post by aysiu on 2006-11-02
> **Roque said:**
> That's a good idea: the test user's KMenu works OK.
In that case, log into your old user and try this: ```
mv ~/.kde ~/.kde.old
``` and then log out and log back in again.

---

### Post by Roque on 2006-11-02
Strange. That didn't work. All my KDE settings have been reset (as expected) but the problem persists. I had to create a new user and adjust all the settings from scratch. Now KMenu works, but I don't have sound enabled:

"xine was unable to initialize any audio drivers."

(it worked perfectly before). Let's see if I can fix this new one.  :)

Anyway, thanks for your help!

---

### Post by aysiu on 2006-11-02
Make sure your new user belongs to the *audio* group: ```
sudo adduser *username* audio
```

---

### Post by kerry_s on 2006-11-02
Make sure your new user is in the admin group, if you intend on deleting the old one.

---

### Post by Roque on 2006-11-02
Aysiu, 
That was it. Honestly, I wouldn't have thought that one *in a million years*. Thank you again for your great help!

Kerry_s,
Thanks; fortunately (and just in time ;) ) I noticed that admin rights were going to be necessary.

---

