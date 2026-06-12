---
title: "Weird wastebasket behavior"
date: 2006-06-15
forum: Desktop Environments
---

### Post by Joe Momma on 2006-06-15
Ok, so maybe this isn't the most critical thing in the world, but it still bugs me, and I would like to fix it.  I searched the forum already and didn't see anyone else mention this.

I am running ubuntu 6.06, updated via apt from 5.10.

I recently created a new user on my machine and set everything up identically to my first user.  In doing this I put the wastebasket on the desktop, because that's where I like it.  Now under this second user if I try to empty my wastebasket I get an error message saying "error while deleting" and the buttons "skip cancel retry".  Hitting "retry" just gives me the error again, while the other two make it go away.  However no matter what button I hit, the wastebasket gets emptied.  So I have no idea what error it is talking about.  I can create new files, drag them in there and repeat this all day.  It's not just a rare fluke.

Now if I try to empty the wastebasket from the trash can in the corner of the bottom toolbar, I don't get this error.  I never noticed this error under the beta version, but then again it doesn't happen under the other user on my machine, or the taskbar wastebasket either. 

Like I said, nothing critical, but something has a glitch in it somewhere (quite possibly my fault).

Anybody have any ideas?

---

### Post by meng on 2006-06-15
Are you able to (with that second account) go to terminal, and
```
cd ~/.Trash
rm -rf *
```
Sometimes if there are files in Trash that the user does not have permissions to delete, then it will not work. However, IIRC, it doesn't spit out an error message, it just doesn't empty the trash. So that may NOT be the problem, but it's still worthwhile trying to empty it manually I think.

---

### Post by Joe Momma on 2006-06-15
Yup, that works fine.

In fact I can even move the whole .Trash directory to a temporary location and then try deleting something else.  It makes a whole new .Trash directory in my home directory, which also gives me the "error while deleting" message when trying to empty it... but only from the desktop icon, not the taskbar one.

It's weird, and nothing I can't live with... but I want it perfect.

I'm such a whiny little bitch ;)

---

### Post by meng on 2006-06-15
Of course you should demand perfection. I somehow suspected my suggestion wouldn't be a permanent fix. Myself, I hate how the Recent Documents function is still buggy.

---

### Post by Joe Momma on 2006-06-21
ok I think I figured out what is causing the problem, if anyone is interested.

I have 2 hard drives in my machine.  The second one (also ext3) is mounted as /storage.

It seems that I deleted a file off of /storage as "user1" and Ubuntu made a local trash directory called  "/storage/.Trash-user1"

When I log in as "user2" and attempt to empty the trash it says it failed.  It gave me the same "cancle or retry" error as before.  But I noticed that if I unmount /storage this error does not appear.  When I remount it, I get an error about not having permission to modify the parent directory.  So then I tried doing a 

       "sudo chmod 777 /storage/.Trash-user1"

This also let me empty the trash as user2 without an error.

Not sure if this is a bug, a security feature or just some fluke on my machine.  But I have seen some other people mention they had trash can pemission problems too.  

Can anybody else confirm this?

---

