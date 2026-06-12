---
title: "sudo and su"
date: 2009-02-15
forum: General Help
---

### Post by iblazev on 2009-02-15
Hello!
Something puzzles me with sudo and su commands.
I have 2 users on a Hardy system: user1 and user2.
user1 was first created and so he was in admin group from the start and sudo works without problems. Now, when I added user2 and add him to admin group - he still cannot use sudo. The pass for user2 isn't recognized. 
That's my first puzzle:/ 

For the second puzzle - if I need to switch users with su command, I need to use: 
*sudo su "user"*
but if I need to switch to root, all I need is _su_.

Anyone has some ideas or is this default on Ubuntu?

---

### Post by hansdown on 2009-02-15
Hi iblazev.

This explains some of what you need.

[http://bst-softwaredevs.com/apps/articles/ubuntu-8-04-sudo-user.html](http://bst-softwaredevs.com/apps/articles/ubuntu-8-04-sudo-user.html)

---

### Post by iblazev on 2009-02-15
This explains some of what you need.

[http://bst-softwaredevs.com/apps/articles/ubuntu-8-04-sudo-user.html](http://bst-softwaredevs.com/apps/articles/ubuntu-8-04-sudo-user.html)[/QUOTE]


Thanx! That does makes clear the first part. 
But I'm still puzzled why second user cannot use sudo although he is in admin group like first user and adnim group is defined as one with root privileges in sudoers.

---

### Post by hansdown on 2009-02-15
I'm not able to give you a good answer, but this is something I should learn more about. 

This explains a little more, but I need to look more.

---

### Post by hansdown on 2009-02-15
Sorry if it seems I'm just throwing things at you, but this free guide download is a gold mine of info.. Hope it helps.

[http://www.ubuntupocketguide.com/download2.html](http://www.ubuntupocketguide.com/download2.html)

Many thanks to Keir Thomas for this.

---

### Post by iblazev on 2009-02-15
Thanx very much:)
Will look into it.

---

### Post by bodhi.zazen on 2009-02-15
I think your confusion comes from mis-understanding the difference between sudo and su. This is easy to do since both commands are used most commonly to give root access.

su = switch user

su - == enter root's password and you obtain a shell as root.

su user2 == enter user2's password and you obtain a shell as user2

If you can su root that implies you set a root password.

sudo = switch use do

sudo command = enter your users password (not root's) alows you to run the said command as root

sudo -u user2 command = enter your users password (ont user2's) to run the command as user2

See also : [https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

====

Now as to your problem, if use2 cannot run sudo either :

1. sudo is not configured properly. user2 needs to be in the admin group. After changing groups you need to log off and back in.

2. You are entering the wrong password. You need the correct password.

---

### Post by iblazev on 2009-02-15
> **bodhi.zazen said:**
> I think your confusion comes from mis-understanding the difference between sudo and su. This is easy to do since both commands are used most commonly to give root access.

su = switch user

su - == enter root's password and you obtain a shell as root.

su user2 == enter user2's password and you obtain a shell as user2

If you can su root that implies you set a root password.

Well, that was what I expected BUT *su user2* doesn't work when called from user1, all I got is authentication failure and I really watched not to mistype the password. I tried it several times and only way I can change from user1 to user2 is with *sudo su user2*.
*su* by itself, however, works ok. Root pass is typed and I switch to root. Only switch between user1 and user2 is somewhat funny...

> 
sudo = switch use do

sudo command = enter your users password (not root's) alows you to run the said command as root

sudo -u user2 command = enter your users password (ont user2's) to run the command as user2

See also : [https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

====

Now as to your problem, if use2 cannot run sudo either :

1. sudo is not configured properly. user2 needs to be in the admin group. After changing groups you need to log off and back in.

2. You are entering the wrong password. You need the correct password.

I did read rootsudo and looked few posts regarding addin user to sudoers list here on forum but that didn't help me much. 
It isn't great wisdom to add user to admin group and theoretically, that should do it for sudo to work...

For 1 and 2 - that's the problem. user2 IS IN admin group as I mentioned before. There is little chance that I mistyped the pass EVERY time I tried.

---

### Post by iblazev on 2009-02-15
Ok. It looks that something is wrong with the user2 acc. I added user3 and put him in admin group and sudo for him works fine. 
Now I'm puzzled what can make user2 acc to behave in that way...

---

