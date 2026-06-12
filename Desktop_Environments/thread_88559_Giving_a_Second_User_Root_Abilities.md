---
title: "Giving a Second User Root Abilities??"
date: 2005-11-10
forum: Desktop Environments
---

### Post by Georgie-o on 2005-11-10
__Is it possible to give a second user the rights to do _all_ admin functions _and_ log in as Root using "sudo"?

Thanks

---

### Post by invalid on 2005-11-10
You will need to either put the second user into an "admin" group, or give them explicit access in the sudoers file.

```
sudo visudo
```

Cheers,
Cb

---

### Post by Georgie-o on 2005-11-10
how do you designate which user get's Root abilities by typing:

"sudo visudo"

does it then ask which user?

Thanks

---

### Post by SickTwist on 2005-11-10
Adding the user to the admin group is the preferred way in Ubuntu. Do this as a user who already has administration priviledges:

System --> Administration --> Users and Groups

Click on the "Groups" tab, select "admin" from the list, and click on "Properties".

Now you can select the user's name from the "All users" list and click the "Add" button to add this user to the admin group. Users can be removed by selecting the user's name from the "Group members" list and clicking on "Remove".

Click "OK" when finished and click "OK" on the "Users and Groups" window.

---

