---
title: "Using GAIM with multiple logins"
date: 2005-12-15
forum: Desktop Environments
---

### Post by xftnfnb7 on 2005-12-15
I am current using GAIM (nice product by the way) with AIM.  If I login in as user "A" and set up a buddy list all the other users on the system share the same buddy list.  Is there a way for each user to have their own buddy list?

---

### Post by cstudent on 2005-12-15
I place my buddies in groups by protocol. I have groups called Yahoo, MSN, Google, AIM, ICQ, etc. I also have it setup to only show online buddies and groups so the list is not so cluttered.

---

### Post by xftnfnb7 on 2005-12-15
That works. But I share this computer with my 10 year old and I really don't what her sharing my buddy list.

---

### Post by cstudent on 2005-12-15
Create a new user account for your yougin'.

---

### Post by towsonu2003 on 2005-12-15
[QUOTE=xftnfnb7]That works. But I share this computer with my 10 year old and I really don't what her sharing my buddy list.[/QUOTE]
lol heheh

you could use an alternative chat thing (not sure which, just take a look at synaptic for 'messaging') and even change permissions of folder ~/.chatthingprogram so that s/he won't be able to open your chat thing. 

or you could just gve him/her a username (which is much more easier) and separate what you two are doing for good. + you can forbid him/her from even looking at your files all toghether by changing read permissions of your home directory, while keeping your read privileges on his/her home directory as you'll be a sudoer...

edit// I hate when someone posts while I am still typing :PpPp

---

### Post by xftnfnb7 on 2005-12-15
I tried that.  I actually have 4 logins on the machine.  Any login I create seems to have access to any of the "Buddies" I create.

---

### Post by cstudent on 2005-12-15
Hmmmm. I just created a test user account and logged in. I went to Gaim and it wanted me to add an account. I can see it having the same buddies if you enter the same account names, but not if you enter just the accounts for your 10 year old. Unless your child's account also has the same buddies included.

---

### Post by towsonu2003 on 2005-12-15
[QUOTE=xftnfnb7]I tried that.  I actually have 4 logins on the machine.  Any login I create seems to have access to any of the "Buddies" I create.[/QUOTE]
not supposed to happen :)
try this (to restrict read access of others) as the first user (sudoer) ```
sudo chmod -R o-rwx /home/username/.gaim
``` for each username you got. Then set up gaim accounts from scratch for each users separately, from their respective accounts (i.e. log in as 10 yr old, set up his/her gaim account + buddies; log out; log in as you; set up you account + buddies etc.). 

I am assuming, because gaim's settings will be separate for good for each account, the only way you will share buddies will be setting up gaim for 2+ users from same 'gnome' (read: computer) account (in this case, you dont wanna do that).

---

### Post by xftnfnb7 on 2005-12-16
Thanks for the help.  I discovered that if you use the same AIM account in two different logins the buddies are shared.  So I set up my daughters own account and we now have seprate buddies.  

Thanks
:D

---

