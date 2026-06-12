---
title: "Unable to create user - already exists"
date: 2009-04-29
forum: General Help
---

### Post by jonboy99 on 2009-04-29
Hi folks, after a reinstall I kept a separate home partition, which had some preexisting users folders already in it.
I am trying to recreate a user account for one of those users, but even though I have deleted his directory in home (so I can create a new one) it keeps telling me the user already exists so I can't use that name.  However it doesn't appear on the list of users in the 'users and groups' menu.

Is this list of users kept elsewhere and got missed somehow, can I manually delete it?

Thanks
Jon

---

### Post by oOarthurOo on 2009-04-29
You might have a problem with the user id number. When you try creating the new user, don't let ubuntu automatically choose the number for you, instead, increment it by 5. You'll find it under the advanced tab. By default, the first user is given an id of 1000.

Also, just make sure you've cleaned up things properly. Use ls -a in the terminal from /home to ensure you haven't missed anything.

---

### Post by jonboy99 on 2009-04-29
Cheers, I'd forgotten to delete the group with the same name as the user.  Once i'd done this I was able to recreate the user with the same name.

---

### Post by oOarthurOo on 2009-04-29
Glad my rambling guesswork helped you find the correct solution. ;)

Perhaps mark the thread as solved to help future users find solutions quicker.

---

### Post by psrdotcom on 2011-09-18
Thanks ..

---

