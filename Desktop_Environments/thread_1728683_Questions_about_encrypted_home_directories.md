---
title: "Questions about encrypted home directories"
date: 2011-04-14
forum: Desktop Environments
---

### Post by blenderfox on 2011-04-14
Hi there,

I have a few questions about the encrypted fs, specifically about home directories.

When I installed Ubuntu, I selected to have my home directory encrypted which is fine.

Now, I want to create a new user, and copy some of my files to that home directory, but I want to keep that home directory encrypted also.

I was thinking maybe I should copy out of the home directory to a shared location, then copy it into the second user's home directory, but if I do that, the data is in the clear (unencrypted).

Is there a way I can "connect" to the second user's encrypted home directory and copy into there from my account or vice versa?  Or do I have to decrypt my home directory, access it from the second user and copy that way, before re-encrypting my home directory again?

I've seen posts about recovering passwords from encrypted filesystems, wrapping, unwrapping, and rewrapping, but I don't know what that's all about, nor whether it is relevant to what I'm trying to do? At the moment, there's no problem accessing the home directories from the relevant user accounts. So I can access mine, the second user can access hers, but it's just connecting the two that I don't know how to do. :P

Hope this makes sense :P

---

### Post by Gnofwarwick on 2011-04-14
It's simpler than that.

As both hard disc directories are encrypted all data stored there is encrypted and un encrypted (using the appropriate key) when it is read.

You can do a_ straight copy_ from your home directory to the target directory and it will be correctly encrypted at the target end. 

Uf you have write permission to the new user directory, you can use the GUI desktop to do the copy. 

If you do not have write permissions to the new users directories, you will have to use the command line and sudo cp <my file> <new user file>.

---

### Post by blenderfox on 2011-04-14
> **Gnofwarwick said:**
> It's simpler than that.

As both hard disc directories are encrypted all data stored there is encrypted and un encrypted (using the appropriate key) when it is read.

You can do a_ straight copy_ from your home directory to the target directory and it will be correctly encrypted at the target end. 

Uf you have write permission to the new user directory, you can use the GUI desktop to do the copy. 

If you do not have write permissions to the new users directories, you will have to use the command line and sudo cp <my file> <new user file>.

So all I do is copy into the second user's home directory? Does ubuntu auto-encrypt there and then, or does it encrypt at the next user login?

Thanks for the quick reply, though :)

---

### Post by movieman on 2011-04-14
> **momokoyukino said:**
> So all I do is copy into the second user's home directory?

The other user has to be logged in at the time, otherwise their home directory won't be unencrypted.

---

### Post by blenderfox on 2011-04-15
Ah. So both users need to be logged in before we can transfer between each other. Makes sense. Thanks for the help! :)

---

