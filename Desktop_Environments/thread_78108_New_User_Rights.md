---
title: "New User Rights"
date: 2005-10-17
forum: Desktop Environments
---

### Post by desertViking on 2005-10-17
Hi,

I created a new user accunt, and I'm fairly new at administrative stuff.

For my account, it was set up during the installation as the primary user.  Using this account, whenever I want to run any of the adminstrative programs like user manager, it prompts me for the root password, which I've set using sudo passwrd yadayada.

I've created a new account and made it part of my group, but whenever I run a program that requires administrative privileges, I enter yadayada, and it fails authentication.

I'm missing something here, what is it?

Thx!

desertViking

---

### Post by bluck on 2005-10-17
[QUOTE=desertViking]Hi,

I created a new user accunt, and I'm fairly new at administrative stuff.

For my account, it was set up during the installation as the primary user.  Using this account, whenever I want to run any of the adminstrative programs like user manager, it prompts me for the root password, which I've set using sudo passwrd yadayada.

I've created a new account and made it part of my group, but whenever I run a program that requires administrative privileges, I enter yadayada, and it fails authentication.

I'm missing something here, what is it?

Thx!

desertViking[/QUOTE]

if you type in the terminal `id YOURUSER` you will see that your initial user was made a member of many groups, notably 'adm' and 'admin'

plus some others which allow access to various operations.

---

### Post by dbott67 on 2005-10-17
By default, only the first user created during installation will be allowed to install software or make system modifications.

All other users that are created will not have the appropriate permissions.  You could always add them to the "**admin**" group in **System --> Administration --> Users & Groups.**

If you check the "Show all users and groups", there are a bunch of hidden groups that your user account is a member of.  I'm not sure which groups you would need to add them to (all of them? just admin?), but if you added the secondary account to all of the same groups, you should be able to do what you need.

-Dave

---

