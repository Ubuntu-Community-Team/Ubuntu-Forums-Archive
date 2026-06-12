---
title: "Problem when creating new users"
date: 2005-12-09
forum: Desktop Environments
---

### Post by fabriciobraga on 2005-12-09
Hi all,

I'm new to Ubuntu Linux, and I having a big trouble to create new user accounts.

The intallation did works fine, and my Ubuntu seems to be ok.  But when I create a new user account I got an error when try to make 1st login.  Ubuntu gives me a warning telling that the /home/newuserdir don't exists!

I have tried to create new user accounts two ways, first using command line:
$ useradd somenewuser
and then:
$ passwd somenewuser
and setting password here...

When I tried to proceed login, I got that message (or somethig like that).

Then I tried to create using "User and Groups" administration tool, at "System" menu of Gnome Graphical Interface, but the same error occours...

Somebody can help me?

Regards,
Fabricio Braga

---

### Post by tomski on 2005-12-09
try typing : 

$ adduser 

it should then turn into a wizard and ask you the question needed to create a user

if that dont work try creating the home folder first thus :

$ mkdir /home/user
$ useradd user
$ passwd user

if still no joy repeat process but as root

---

### Post by fabriciobraga on 2005-12-09
Thanks!!!  

I've tried the "adduser" command instead "useradd"...  after give some information to the command line wizard the new login was fine.

I still don't know why the command "useradd" was not working right, but now it doesn't matter.

Thank you tomsky!

Regards,
Fabricio Braga

---

