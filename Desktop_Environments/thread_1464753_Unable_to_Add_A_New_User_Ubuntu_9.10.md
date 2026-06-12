---
title: "Unable to Add A New User Ubuntu 9.10"
date: 2010-04-28
forum: Desktop Environments
---

### Post by RyFo18 on 2010-04-28
I am trying to add new users to Ubuntu 9.10.  I go into the Users & Groups GUI, click the keys to authenticate and then press 'Add User'.

I enter the following:

Username: guest1
Real Name: guest1
Profile: Desktop user
Password Info

One the Advanced tab:
Home Directory: /cltrain2_home/guest1
Shell: /bin/bash
Main Group: root
User ID: 1001

I click OK and I can see the new user added to the User Settings dialogue.  All seems to be well.  When I click close, it does not appear that this user is ever added.  I checked in the /cltrain2_home directory and I do not see the guest1 home directory.  When I open up Users & Groups again, the user is now mysteriously gone.

---

### Post by RyFo18 on 2010-04-28
Nevermind, I figured it out.  I was able to add new users using the 'useradd' command.  

The main reason the GUI wasn't working was because NIS was enabled.

---

