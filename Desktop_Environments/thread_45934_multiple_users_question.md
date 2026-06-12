---
title: "multiple users question"
date: 2005-07-02
forum: Desktop Environments
---

### Post by not_yet on 2005-07-02
hello,

I have 3 users on one machine, each user has thier own log in and password

when I try to make changes for the other 2 users ( not the main user) the system won't allow it?

for example each user has a firefox profile

how do I adjust the profiles for the other users

I'd like to do this without giving the other users sudo rights?

thanks

---

### Post by desdinova on 2005-07-02
[QUOTE=not_yet]hello,

I have 3 users on one machine, each user has thier own log in and password

when I try to make changes for the other 2 users ( not the main user) the system won't allow it?

for example each user has a firefox profile

how do I adjust the profiles for the other users

I'd like to do this without giving the other users sudo rights?

thanks[/QUOTE]

The idea of users having their own login is to ensure they cannot affect each other - if you want to learn moer about giving users permissions to each others files - install RUTE via synaptic which will give you detailed info on the 

chmod
chown 

commands, which combined with user groups will do what you want.

---

### Post by Juergen on 2005-07-02
> when I try to make changes for the other 2 users ( not the main user) the system won't allow it?You login as another user and then you can't change files in ~otheruser?

Or do you try to write in another user's ~? 
You don't have permissions to do so, use sudo. This is an admin-task
> I'd like to do this without giving the other users sudo rights?The others don't need to be sudoers, but you have to use it.

---

### Post by crashtest on 2005-07-02
[QUOTE=not_yet]hello,

I have 3 users on one machine, each user has thier own log in and password

when I try to make changes for the other 2 users ( not the main user) the system won't allow it?

for example each user has a firefox profile

how do I adjust the profiles for the other users

I'd like to do this without giving the other users sudo rights?

thanks[/QUOTE]


sudo su - <username> will switch you to the other user, in the other user's environment.  The space before and after the '-' is important.

Try this, then issue the command 'id' which will display your user and group ID.  You will see that you have become the other user.

---

