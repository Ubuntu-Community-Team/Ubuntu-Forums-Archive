---
title: "Is there a way to list users in a group?"
date: 2009-06-17
forum: General Help
---

### Post by adamforum on 2009-06-17
I see that you can list what groups a user belongs to via "id <user>" or "groups <user>" -- is there a command that takes a group name and displays all it's members?

---

### Post by capscrew on 2009-06-17
> **adamforum said:**
> I see that you can list what groups a user belongs to via "id <user>" or "groups <user>" -- is there a command that takes a group name and displays all it's members?

Yes there is.  From the terminal try```
getent group
```  If you need to do this as root then add sudo in front of the command.

---

### Post by _Purple_ on 2009-06-17
You can go to System > Administration > Users and groups, click on manage groups. Properties will show you the group members. 

You can also install the package named members.
```
sudo apt-get install members
```
Then to find the members of a specific group
```
members <groupname>
```

---

