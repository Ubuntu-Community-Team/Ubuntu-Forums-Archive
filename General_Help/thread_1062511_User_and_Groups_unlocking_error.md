---
title: "User and Groups unlocking error"
date: 2009-02-07
forum: General Help
---

### Post by Schok on 2009-02-07
Everytime i try to unlock in System > Administration > Users and Groups
i get this error:
```
Could Not Authenticate
an unexpected error has occured
```

how can i fix it? i can't change any settings if i don't unlock.

---

### Post by Tim Sharitt on 2009-02-07
Did you get to the point where you can enter your password?

---

### Post by Schok on 2009-02-07
no i didn't. just the error.

fyi, this has never happened until recently. not so sure about what i did to produce that error though..i hope its fixable

---

### Post by Schok on 2009-02-07
I was able to unlock after a recovory mode reboot > normal boot surprisingly BUT after i tried to use ubuntu tweak "Applications" unlock button the error came out again and NOW the error comes out from Users and Groups too.

So i think its a Ubuntu Tweak bug..

---

### Post by Simpleton on 2009-02-14
I've got exactly the same problem. I'm a bit useless at sorting some of these issued. Tried the recovery mode, no help.

Can anyone help me???

---

### Post by Simpleton on 2009-02-17
Sorted what you do is this

1. go to recovery mode
2. Select root command prompt
3. type in

sudo adduser **you current user name** admin

4. reboot

You will have your prviileges back. I suggest then making a 2nd admin account incase it ever happens again!

---

### Post by Schok on 2009-02-19
my user is already added as admin..

---

### Post by Simpleton on 2009-02-19
yeah, mine was too. But what you will probably find is that it has gone a bit wrong and taken you off the admin duty. Which is what happened to me.

Have you tried what I have suggested?

---

### Post by Schok on 2009-02-19
no, what i meant was it stated that the user has already been added as admin..so i guess that is not the problem..

---

### Post by jschodde on 2009-02-22
Simpleton: Your steps worked for me. Thanks!

---

### Post by jespes on 2009-03-15
hi,
i'm having the same problem --can't make changes in "users and groups," and i get this same error message.

booting in recovery mode and adding MYUSERNAME to the admin group doesn't fix it; i have the same problem still.

yikes? any suggestions? many thanks.

this is a very new install of ubuntu 8.10 desktop, only a week or so old.

EDIT/UPDATE:
I tried going into recovery mode and creating a temporary new admin-level user, TESTUSER, to see if the problem occurs when signed on as TESTUSER. and it does have the same problem.

---

### Post by Schok on 2009-03-15
any luck?

---

### Post by theozzlives on 2009-03-15
> **jespes said:**
> hi,
i'm having the same problem --can't make changes in "users and groups," and i get this same error message.

booting in recovery mode and adding MYUSERNAME to the admin group doesn't fix it; i have the same problem still.

yikes? any suggestions? many thanks.

this is a very new install of ubuntu 8.10 desktop, only a week or so old.

EDIT/UPDATE:
I tried going into recovery mode and creating a temporary new admin-level user, TESTUSER, to see if the problem occurs when signed on as TESTUSER. and it does have the same problem.

How do you add yourself to the admin group  if you can't  change users and   groups?

---

### Post by Schok on 2009-03-15
if im not mistaken u can do it on the terminal like this:
```
useradd -m yournewuser
passwd yournewpassword
adduser yournewuser admin
reboot
```

not sure if u need to login to root to do that or just sudo it..there's a thread somewhere about this

---

### Post by jespes on 2009-03-16
> **Schok said:**
> if im not mistaken u can do it on the terminal like this:
```
useradd -m yournewuser
passwd yournewpassword
adduser yournewuser admin
reboot
```

not sure if u need to login to root to do that or just sudo it..there's a thread somewhere about this

that's precisely what i tried: i went into Recovery Mode and used terminal commands to create a new admin user. then i did a normal reboot and signed on as this newly created admin user, in hopes i'd be able to regain admin authority in the "users and groups" panel. 

but it didn't work: i still had the same "can't authenticate" problem when logged in as the new user.

separately i also tried booting in Recovery Mode and reassigning my original username to "admin." but that didn't have the desired effect either.

bottom line: the "users and groups" panel is non-functional for me. i can't create new users, and i can't modify any of the user settings there. each time i try, i get the "can't authenticate" error described at top of this thread.

---

### Post by Schok on 2009-03-16
do u have ubuntu tweak installed?

---

### Post by jespes on 2009-03-16
> **Schok said:**
> xxx ubuntu tweak ? xxx

ah, i'm unfamiliar with ubuntu tweak. does it address this issue? (i just a superfast google on it and didn't turn up an answer ...)

---

### Post by Schok on 2009-03-16
this problem emerged after i started using ubuntu-tweak..so i guess thats not the problem

---

### Post by mthelms on 2009-08-10
> **Simpleton said:**
> Sorted what you do is this

1. go to recovery mode
2. Select root command prompt
3. type in

sudo adduser **you current user name** admin

4. reboot

You will have your prviileges back. I suggest then making a 2nd admin account incase it ever happens again!

I first starting encountering this problem when I created a 2nd admin account (perhaps i shouldn't have called it admin?).  This fix got me back to normal, though.  Thanks!

---

### Post by ScottyP on 2009-10-09
> **mthelms said:**
> I first starting encountering this problem when I created a 2nd admin account (perhaps i shouldn't have called it admin?).  This fix got me back to normal, though.  Thanks!

I think that was my problem, too. No more "admin" accounts for me. From now on they're "superduck" or something. :D

---

