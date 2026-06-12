---
title: "Accessing Users and Groups - please help!"
date: 2009-02-13
forum: General Help
---

### Post by Clayton South on 2009-02-13
Hi everyone, 

I just switched over to Intrepid 8.10, from Hardy 8.04.  When i was running 8.04 and wanted to make myself administrator, I would go to System - Administration - Users and Groups and highlight my name, click unlock, and then it would ask the administrator (my wife) for the password, after which time I would go and change myself to admin in my own account.

Now, under the same user setup, when I go in 8.10 to do the same thing, I get this message:

"The configuration could not be loaded. You are not allowed to access the system configuration."

Now, when I logged in under her account and made myself admin via the same method outlined above, and logged back in under my own account, the menu would load.

So my question is: is this normal for 8.10? And, how do I make it so that I can do what I outlined above - as in 8.04 - so that I dont have to log in and out many times just to make myself the admin?

thanks!

-Clayton South

---

### Post by Old *ix Geek on 2009-02-14
I don't use Gnome, but this concept should apply regardless: Once you set a user's privileges, they should stick.  In other words, there shouldn't be any need to continually set them again.  So I'm confused as to why you're doing this.

---

### Post by Clayton South on 2009-02-14
I'm doing this because I am not the admin - sometimes I need to be in order to run updates and the like. In 8.04, in my account, I can simply go into Users and Groups, click unlock, select the user who is admin - my wife - she enters her password, I highlight my account, click a tab and select "administer system" and then I have admin access to do updates and install / ununstall etc. 

When I try to do this in 8.10 it keeps telling me that I can not access system configuration. 

How can I get around this?

-Clayton South

---

### Post by dcstar on 2009-02-14
> **Clayton South said:**
> I'm doing this because I am not the admin - sometimes I need to be in order to run updates and the like. In 8.04, in my account, I can simply go into Users and Groups, click unlock, select the user who is admin - my wife - she enters her password, I highlight my account, click a tab and select "administer system" and then I have admin access to do updates and install / ununstall etc. 

When I try to do this in 8.10 it keeps telling me that I can not access system configuration. 

How can I get around this?

-Clayton South

Accounts are not meant to be continually switched from admin to non-admin rights, it is an obvious security hole that could lead to problems because someone might "forget" that they have left admin rights on an account that should not have them.

If you want admin rights to do software installs, simply set up a new account with those rights and log into it whenever you need to do this stuff.

---

### Post by Clayton South on 2009-02-15
> **dcstar said:**
> Accounts are not meant to be continually switched from admin to non-admin rights, it is an obvious security hole that could lead to problems because someone might "forget" that they have left admin rights on an account that should not have them.

If you want admin rights to do software installs, simply set up a new account with those rights and log into it whenever you need to do this stuff.

Thanks for the reply. 

I do understand that it "could" be a problem, but not in this situation.  

How can I make it so that the org.freedesktop.systemtoolsbackends.set is in 8.10 like in 8.04?

Thanks!

-Clayton South

---

### Post by Clayton South on 2009-02-15
bump

---

### Post by Ingenium on 2009-02-15
I'm also having the same issue. I actually can't access most things under System, Administration. I'm trying to delete a user, and I know that it can be done from the command line which is what I will end up doing, but this is still a problem.

---

### Post by Old *ix Geek on 2009-02-15
> **Clayton South said:**
> I'm doing this because I am not the admin - sometimes I need to be in order to run updates and the like. In 8.04, in my account, I can simply go into Users and Groups, click unlock, select the user who is admin - my wife - she enters her password, I highlight my account, click a tab and select "administer system" and then I have admin access to do updates and install / ununstall etc. 

When I try to do this in 8.10 it keeps telling me that I can not access system configuration. 

How can I get around this?

-Clayton SouthLike I said, users' privileges aren't MEANT to continually be changed.  Just set your rights the way you want them and be done with it.  If you don't want your normal user account to ALWAYS have admin privileges, then do as dcstar suggested and create an additional account.

---

### Post by Ingenium on 2009-02-16
Problem was fixed following directions here: [http://ubuntuforums.org/showthread.php?t=779992](http://ubuntuforums.org/showthread.php?t=779992)

It was a dbus problem, at least for me.

---

