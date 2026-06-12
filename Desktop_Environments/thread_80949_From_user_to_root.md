---
title: "From user to root ?"
date: 2005-10-23
forum: Desktop Environments
---

### Post by r4ik on 2005-10-23
This question might be asked a million times so forgive me as it has ;) 
In the terminal i can not get root acces.
I used the sudo su- but it still blocks my root password.
Where do i go from here ?

Internet is running e-mail to
howmuch can a neewbie in 48 hours do ?

---

### Post by LorenzoD on 2005-10-23
Works fine here. Make sure you have a space between the su and the -: sudo su -.

---

### Post by r4ik on 2005-10-23
I used the space but it does not work.
Anoying that is because i am not able to
install any software at all.

---

### Post by LorenzoD on 2005-10-23
Can you sudo at all? Remember that by default only the first user you create is made a sudoer(5). Try sudo <some command> to make sure you are able to sudo at least.

If you can sudo <something>, what password do you enter when you do sudo su -. You're performing a sudo, so it should be your user password that you use.

And installing shouldn't be difficult, even without being able to su. sudo apt-get install, or if you're installing self-compiled: sudo make install.

If you're still having probelms, could you post the error output you get?

---

### Post by r4ik on 2005-10-23
Workin on it give me a moment please.

---

### Post by r4ik on 2005-10-23
Here is what is happening

r4ik@computer:~$ sudo su-
Password:

From there i can not enter my password.
 sudo apt-get install flashplayer-mozilla

Same story cannot enter password.:confused:

---

### Post by chinaski on 2005-10-23
what you mean exaclty you cannot enter it?

you get error message?

---

### Post by LorenzoD on 2005-10-23
What do you mean by "cannot enter password"? That you get no visual feedback when you are typing? In that case, it's normal, it won't give you any visual feedback.

As I said earlier, you need to be in the sudoers file to be able to sudo at all. When you installed Ubuntu, you were asked to set up a user account. By default that account has sudo access. Are you using a different user account? Or have you made any changes to the sudo file?

---

### Post by Saiboogu on 2005-10-23
What do you mean by "cannot enter my password" ? 

Sorry, don't mean to point out the obvious - but is it just not showing when you type? That is normal. Are you typing it accurately in one go? Its not very forgiving of typos and backspaces - if you miss-type, best to just <return> and wait for the prompt to come back up.

If you are typing your full user password, and <return> ... What happens next? Does it inform you that the password was bad, or some other error? As others pointed out, only the first user is on the sudoers list by default. If you're using an additional user account, try logging into your original user account, and type:

```
sudo adduser <newacct> admin
```

This should add the new account to the admin group and allow them to sudo. 

Just a few things to try .. In any case, post some more info so we can help more :)

EDIT: Took too long typing, LorenzoD beat me to the point. :)

---

### Post by r4ik on 2005-10-23
Gives no visual reply i would not have figured that one 
out myself for day's.
Thank you so much for your reply.

---

### Post by r4ik on 2005-10-23
[QUOTE=Saiboogu]What do you mean by "cannot enter my password" ? 

Sorry, don't mean to point out the obvious - but is it just not showing when you type? That is normal. Are you typing it accurately in one go? Its not very forgiving of typos and backspaces - if you miss-type, best to just <return> and wait for the prompt to come back up.

If you are typing your full user password, and <return> ... What happens next? Does it inform you that the password was bad, or some other error? As others pointed out, only the first user is on the sudoers list by default. If you're using an additional user account, try logging into your original user account, and type:

```
sudo adduser <newacct> admin
```

This should add the new account to the admin group and allow them to sudo. 

Just a few things to try .. In any case, post some more info so we can help more :)

EDIT: Took too long typing, LorenzoD beat me to the point. :)[/QUOTE]

I will try to be more detailed next time, there is a slight possebility I will
be around more often. :) 
Thanks for youre reply.

---

