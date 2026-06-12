---
title: "Change user"
date: 2014-11-25
forum: Desktop Environments
---

### Post by mayagrafix on 2014-11-25
what is the appropriate way to use more than one account on Ubuntu? should I log out completely from one account before switching to another? or can I have more than one user log in and switch between accounts using  the global system pulldown menu? 

thanks for your help.

---

### Post by carlwsnyder on 2014-11-25
Look at the **su** command.  **su **allows you to _s_witch _u_sers for a series of commands from your present login.  Generally used by users to get root status, but can be used for any general CLI (command line interface, or terminal) command/program.

Generally, you would log out and log back in as the other user when you want to change complete contexts, as in getting email for the new user, change DEs, save documents to the correct Documents folder, etc.

In general, you can have as many user accounts, with whatever limitations or lack thereof, as you wish.  If you want to set up a user to handle just your music collection, or your photographs, you certainly may do so.

---

