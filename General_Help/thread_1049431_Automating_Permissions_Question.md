---
title: "Automating Permissions Question"
date: 2009-01-24
forum: General Help
---

### Post by murmini on 2009-01-24
I have deployed a number of Ubuntu 8.10 machines to the field and they all have been set up with a administrative login (private to us) and a separate user account with password for each machine user.  Unfortunately, we have discovered that the user accounts do not have admin permissions and can not implement upgrades nor can they add or remove software. Can anyone come up with a way that we could deliver a file to those users that would automate the changing of their permissions to include 'admin' so they could update and install/remove software. My hope is that they could download the file to their desktop, run it and effect this change after logging out and back in again. I thank anyone that can help us with this issue.

---

### Post by dcstar on 2009-01-24
> **murmini said:**
> I have deployed a number of Ubuntu 8.10 machines to the field and they all have been set up with a administrative login (private to us) and a separate user account with password for each machine user.  Unfortunately, we have discovered that the user accounts do not have admin permissions and can not implement upgrades nor can they add or remove software. Can anyone come up with a way that we could deliver a file to those users that would automate the changing of their permissions to include 'admin' so they could update and install/remove software. My hope is that they could download the file to their desktop, run it and effect this change after logging out and back in again. I thank anyone that can help us with this issue.

The whole point about security is that only authorised users can make system changes.

Having a system that allows a non-authorised user to make these changes just by downloading a file wouldn't be very secure, so the answer is no - you will have to have someone log into each machine (either locally or remotely) with admin rights and make the changes.

---

### Post by murmini on 2009-01-24
Of course, and that was the plan, I just wondered if it was possible to access the system as a Super user and make that change. We will have to make a 'truck role' to fix this one... Thanks for your help .

---

### Post by albinootje on 2009-01-24
> **murmini said:**
> Of course, and that was the plan, I just wondered if it was possible to access the system as a Super user and make that change. We will have to make a 'truck role' to fix this one... Thanks for your help .

You want them to be able to become root in all cases ?
Or just for installing software ?

If the latter, then add them to the sudoers file for just synaptic package manager.
Check the examples in :
```

man sudoers

```
Then use :
```

export EDITOR=nano
sudo visudo

```
to add a line for them.

Here's an example for those users :
```

john ALL = /usr/sbin/synaptic
james ALL = /usr/sbin/synaptic

```

---

### Post by blackened on 2009-01-24
If these machines are network accessible, then it should be easy to log in remotely and update them. Granted they'll have to be set up for ssh access and security, but you could roll this out on all new machines with a fair amount of ease.

---

### Post by murmini on 2009-01-25
Thanks for all the help!

These machines are not available via a network and I think it would be too complex to instruct the users (beginners) to set them up that way.

From what I understand, the machines will need to be configured to where the users has Admin rights so as to be able to add/remove software and carry out updates.

Obviously, we could instruct them to log out, log in with a provided admin name and password, change their individual user rights to 'Admin', log out and re-log in as the original user.  I was hoping we could simply instruct them to go to the terminal, type in commands and the original admin password, and affect this change. 

The issues involve skill level and I thought the terminal approach with a well written procedure would be the easiest and safest.

Thank you

---

### Post by albinootje on 2009-01-25
> **murmini said:**
> 
The issues involve skill level and I thought the terminal approach with a well written procedure would be the easiest and safest.


If you want them to use a terminal, here's an example, where user "jane" has admin rights, and "tom" has not yet admin rights :

1) they open a terminal
2) they type the following :
```

su - jane
(after this they (tom) fill in the password for jane, which they got from you)
sudo adduser tom admin
(sudo asks here again for the password of jane)

```
3) after that they (tom) log out, and log back in, and they check whether they have admin rights now :
```

groups

```

---

### Post by murmini on 2009-01-25
Thank you SO much !   This works and is exactly what I was looking for ...

---

