---
title: "lost ability to sudo ... now this"
date: 2012-09-05
forum: Desktop Environments
---

### Post by Mintnacho on 2012-09-05
Lost the ability to sudo. So I put in a liveCD and mounted the partition and made the edits to the /etc/sudoers file that way. 
The changes saved and I now have the ability back to sudo.

But I lost the ability to choose which userid to install gui with. I only get the ability to enter the root password as where I should have the choice box between my users.

[http://imgur.com/hiVDt]("http://imgur.com/hiVDt")

---

### Post by Bashing-om on 2012-09-05
Mintnacho;

?? I really do not understand what you are asking.
As you are aware, only root may make ANY system alterations.

1. What version are you using.
2. What desktop do you have, Are you attempting to install alternate desktops for alternate users ??

Without pertinent info pertaining to the particular problem, Cannot offer a diagnosis.

[INDENT]regards <==BDQ

[/INDENT]

---

### Post by ajgreeny on 2012-09-05
I don't understand either, but you talk about a "root password".

Have you enabled the root account on your machine?  If you have you may have changed the way sudo is managed by the system, as by default the root account is disabled in Ubuntu.

Please tell in more detail what is the problem.  This paragraph
> But I lost the ability to choose which userid to install gui with. I  only get the ability to enter the root password as where I should have  the choice box between my users.makes no sense at all to me.

---

### Post by sisco311 on 2012-09-05
You have to add your user to the **admin** group.

---

### Post by Mintnacho on 2012-09-05
> **sisco311 said:**
> You have to add your user to the **admin** group.

sisco 
sudo usermod -aG hfic0 Admin still doesn't bring back the option to select the account.

---

