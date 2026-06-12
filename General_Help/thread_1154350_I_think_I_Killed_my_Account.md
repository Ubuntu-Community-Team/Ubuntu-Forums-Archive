---
title: "I think I Killed my Account"
date: 2009-05-09
forum: General Help
---

### Post by Tapetape on 2009-05-09
I think I killed my user account. I was attempting to make my account safer to use, and I think I did something really stupid. I put my user account, in a different 'group' then my root/admin account, and now when I sudo anything, it says "This account is not in Sudoers File." This also limits my access to any of the administration programs like Synaptic, and the users/groups aswell. Any idea how I can undo my stupidity?

---

### Post by chriskin on 2009-05-09
> **Tapetape said:**
> I think I killed my user account. I was attempting to make my account safer to use, and I think I did something really stupid. I put my user account, in a different 'group' then my root/admin account, and now when I sudo anything, it says "This account is not in Sudoers File." This also limits my access to any of the administration programs like Synaptic, and the users/groups aswell. Any idea how I can undo my stupidity?

i can't seem to remember how to solve it, but i have to bring your hope back, as i recall that most distros do not have the user on the sudoers list by default (fedora for example if my memory doesn't betray me) 
i will google it, if i find anything i will tell you

---

### Post by chriskin on 2009-05-09
Reboot into recovery mode, add your user to the admin group, then reboot to regular mode.

More details here:
[http://www.psychocats.net/ubuntu/sudo](http://www.psychocats.net/ubuntu/sudo)


credit goes to aysiu , i found this at the archives of aysiu's older post on the subject

the answer was that it worked ok

---

### Post by pro003 on 2009-05-09
I think you should get into Recovery mode (from Grub) and then at the menu chose drop to root shell, and then just type:

# sudo useradd -m username
# sudo passwd username

and then just login with the username and pass that you've entered...

---

### Post by geirha on 2009-05-09
Boot into recovery mode to get a root shell, then
```
adduser *your_username* admin
```
should add user *your_username* to the admin group, which in turn will allow your user to use sudo again.

---

### Post by -kg- on 2009-05-09
> **pro003 said:**
> I think you should get into Recovery mode (from Grub) and then at the menu chose drop to root shell, and then just type:

# sudo useradd -m username
# sudo passwd username

and then just login with the username and pass that you've entered...

Substituting "username" above with the username of your user account, of course! Don't just copy and paste! :P

---

### Post by Tapetape on 2009-05-09
Thank you very much everybody, replies were quick! Ill be giving this a try when I get home from work, Thanks ^_^

EDIT: I am home, and I have done as told, and everything is working great :) thank you everyone for the quick, and accurate reply :)

---

