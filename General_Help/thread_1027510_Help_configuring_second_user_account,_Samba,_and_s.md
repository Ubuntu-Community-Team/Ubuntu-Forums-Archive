---
title: "Help configuring second user account, Samba, and shared external HDD"
date: 2009-01-01
forum: General Help
---

### Post by scratman on 2009-01-01
I have created a new user account to allow other users to log into my machine, but I want them to have restricted access, ie, they cannot access my Home Folder.  I also would like to give them access to my external HDD, as currently I am informed that this user does not have the correct permissions.  In addition, I would like to configure my External HDD to be accessible by family members from Windows machines on the home network.  I am sure that this is possible, but I'm currently going round in circles with errors, and banging my head against a wall.  I'd be enormously grateful if somebody could talk me through this.

---

### Post by dcstar on 2009-01-01
> **scratman said:**
> I have created a new user account to allow other users to log into my machine, but I want them to have restricted access, ie, they cannot access my Home Folder.  I also would like to give them access to my external HDD, as currently I am informed that this user does not have the correct permissions.  In addition, I would like to configure my External HDD to be accessible by family members from Windows machines on the home network.  I am sure that this is possible, but I'm currently going round in circles with errors, and banging my head against a wall.  I'd be enormously grateful if somebody could talk me through this.

User accounts without admin rights (which you should NOT assign) only have access to their own /home folders.

You can add users into a Group, and then allow that group access to whatever you like using the properties of things.

Use System-Administration-Users and Groups to do the first two things.

---

