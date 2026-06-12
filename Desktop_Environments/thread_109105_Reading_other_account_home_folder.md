---
title: "Reading other account home folder"
date: 2005-12-27
forum: Desktop Environments
---

### Post by Dearhell on 2005-12-27
I have to accounts in my Ubuntu, the first was added in the installation process and the second one was added in system -> administration -> users and groups after installation

I have no access from the first account login to the home folder of the second account 

I know both logins and passwords

How can I get the permissions to see the second home folder?

Update: I got the solution, I simply had to change permissions with chmod

---

### Post by amohanty on 2005-12-28
> Update: I got the solution, I simply had to change permissions with chmod

I would suggest not doing that. There's a reason why the permissions are set up the way they are. If you need a shared space: 
1. create a folder in /home called common
2. Add yourself and the other user to the **users** group
3. Change the group owner of common to **users** via > sudo chgrp users /home/common
4. Go nuts with the common folder. :)

AM

---

