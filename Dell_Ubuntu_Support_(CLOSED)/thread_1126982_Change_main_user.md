---
title: "Change main user"
date: 2009-04-15
forum: Dell Ubuntu Support (CLOSED)
---

### Post by Derekuda on 2009-04-15
I bought a dell mini with ubuntu, but ended up giving it to my GF.  She wants the computer to have her profile be the default and delete mine.  How does she go about doing that?

---

### Post by antikristian on 2009-04-16
I apollogize if I do not have the correct name for the options here, but my ubuntu system is Norwegian, so the naming is diffrent.

**Change default login:** 
Go to System->administration->login manager (blue icon with dots)
Select security (fifth tab) and change the default user in automatic logins

If you can't see the bottom of the dialog to close it, then move it upwards by holding the alt-key, clicking inside the window and dragging it upwards.

**Allow sudo access**
To be able to do superuser stuff with the new user (remember, you are deleting the old one) go to System-> administration -> users & groups
select unlock and type in your password
Select her accountname and click properties
Select the user permissions tab (third tab)
add her to the "administer the system" group

now test this by opening a terminal and doing a 
```
su <herUsername>
sudo apt-get update
```

If this was successfull after entering her password, then you can proceed with the next step.

**Deleting user**
In the same "users and groups" program
press unlock
delete your old user

---

### Post by antikristian on 2009-04-16
the second and third options can also easily be done through the commandline

[B]
Allow sudo access[/B]
```
sudo usermod -a -G admin <gfUsername>
```
test with 
```
su <herUsername>
sudo cat /etc/sudoers
```
If it didn't work, you won't be able to read the file

[B]
Deleting user[/B]
```
sudo userdel <yourolduser>

```

---

