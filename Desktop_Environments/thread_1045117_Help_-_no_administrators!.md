---
title: "Help - no administrators!"
date: 2009-01-20
forum: Desktop Environments
---

### Post by normanp on 2009-01-20
I am not clear about the status of users in 8.10:
There is a root user but this cannot be enabled to allow login as root as far as I can see. I don't like this as it seems that there is no way to get out of situations as below.

The user created at install seems to be an administrator but when I log in as that user and go to 'Users Settings', create another user called admin, gave it an Administrator profile, then logged on as admin - I found that this user was not allowed access to 'Users settings' - so I assume admin is not really an administrator - so maybe my original user wasn't either!

I now logged in again as my original user, went to 'Users Settings' but could not now unlock it - I get a message 'Could not Authenticate - an unexpected error has occurred' - a rather enigmatic message!

A further mystery is the list of users that drop down top right on the screen - when you choose one and log in does it log off the previous user or not?

This is all confusing - on another machine I managed to remove administrator rights from all users except root and now cannot change any settings (even at the command line).

Finally - using the Authorisations application seems a problem: attempts to use Grant... anywhere are simply ineffective - no message pops up at all!

Thanks for any help.

---

### Post by stefangr1 on 2009-01-20
The root user account is disabled by default, and normal users can perform actions as if they were root using "sudo". If, when using the gui, a password is asked (sometimes you have to click on "Admin" or "Unlock" first), you have to enter your normal user password.

Even though you can enable your root account, you shouldn't because this way of arranging things (which is in clear contrast with windows ways) is an important element of keeping your system secure.

---

### Post by mcduck on 2009-01-20
The problem would be that you created user called "admin", which would by default mean that this user's own group would be called "admin" as well.

However group "admin" is a part of the system, when you give user Administration rights what really happens is that this user is added to "admin" group..

So now you have a group "admin" which actually is related to user called "admin", not to actual group of users with administrator privileges like it should be.

You should be able to fix both problems you described using the recovery mode (selectable from Grub menu during boot) as that will log you in as root user. I'm not absolutely sure how to fix the mess with admin group, though, so hopefully somebody else will be able to give you more exact instructions about that.

---

### Post by normanp on 2009-01-21
Thanks for your quick replies. As it was a new installation I re-installed. In future I won't make a user called 'admin'! I notice that the user created during install is an administrator though the installer (I use the txt installer) implies that it is suitable for everyday use. I would have thought not though - and would create other users with reduced rights for everyday use. First impressions of 8.10 are excellent: I like it that the installer no longer hangs if you don't have an Internet connection + many other improvements.

---

### Post by mcduck on 2009-01-21
Being administrator in Ubuntu is different from being administrator in windows.

In Ubuntu even admin users are not actually running with admin privileges all the time (as they are in Windows). Instead, they only have the right to temporarily gain administrator privileges (by using sudo/gksudo and confirming with a password) to perform admin tasks. Because of this, it's safe to use user accounts with admin rights even for everyday usage.

(Running as root user all the time would be a completely different thing, that's why the root account is locked and even if you enable it you still can't log into desktop as root.)

---

### Post by RedSquirrel on 2009-01-21
@normanp: You might find this helpful:

[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

