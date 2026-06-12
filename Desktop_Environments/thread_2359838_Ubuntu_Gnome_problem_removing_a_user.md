---
title: "Ubuntu Gnome problem removing a user"
date: 2017-04-28
forum: Desktop Environments
---

### Post by rdb3 on 2017-04-28
Ubuntu 17.04 w Gnome.

I had a user that I removed using:
> 
sudo rm -r /home/username

Now when I click on the topbar.... in the button at the far right..... it shows that the user is there.

Next I tried:

> userdel -r username

but that tells me the 'user' does not exist.

I don't know what else to do to get rid of it .  

Thank you in advance.

---

### Post by TheFu on 2017-04-28
You want deluser on debian-based systems.  userdel is "low-level."

According to the manpage, you probably want:```

$ sudo deluser --force --only-if-empty --remove-all-files {username}
```

Then you might want to run ```

$ sudo delgroup --only-if-empty {username}
```
to remove the automatically created per-userid group.

BTW, deleting the HOME without using these tools to do it isn't ideal.
Also, you cannot delete the userid you are currently using.

---

### Post by deadflowr on 2017-04-28
Open Settings  and go to Users.
Click on the *Unlock* icon in the top corner and then select the user and then click on Remove User.

---

### Post by rdb3 on 2017-04-28
> **deadflowr said:**
> Open Settings  and go to Users.
Click on the *Unlock* icon in the top corner and then select the user and then click on Remove User.

Unlocked it but it doesn't let me 'Remove User'...... grayed out.

I think I screwed things up when I deleted home/username.

---

### Post by rdb3 on 2017-04-28
> **TheFu said:**
> You want deluser on debian-based systems.  userdel is "low-level."

According to the manpage, you probably want:```

$ sudo deluser --force --only-if-empty --remove-all-files {username}
```

Then you might want to run ```

$ sudo delgroup --only-if-empty {username}
```
to remove the automatically created per-userid group.

BTW, deleting the HOME without using these tools to do it isn't ideal.
Also, you cannot delete the userid you are currently using.

I just tried sudo deluser...... and got... the user 'username' does not exist.

Tried sudo delgroup .... and got... the group 'username' does not exist.

Yes, using rm  HOME was a bad idea.

---

### Post by deadflowr on 2017-04-28
Then try recreating the directory
```
sudo mkdir /home/username
sudo chown username:username /home/username
```
change username to the user's name.

---

### Post by rdb3 on 2017-04-28
> **deadflowr said:**
> Then try recreating the directory
```
sudo mkdir /home/username
sudo chown username:username /home/username
```
change username to the user's name.

Not working.... getting invalid user.

I think something got corrupted beyond fixable here.
The good thing is that I can still get into the system and everything else seems to be working fine.
At some point in time I may reinstall Ubuntu 17 w Gnome.  It's currently installed alongside Windows 7.
How should I re-install (alongside W 7) so that the new install is completely clean without anything carried over from this current installation?

---

