---
title: "Problem with adding user to group"
date: 2009-02-26
forum: General Help
---

### Post by ThaddeusW on 2009-02-26
Hello everyone,

I am busy working with the Valve Source dedicated server (srcds). My idea is to move the whole srcds install to the /srv directory and then let it be owned by root and the group srcds. I am creating a user called tf2 that will run the server but I am trying to add the user to the srcds group but I cant add the tf2 user to the group. Yes the group was created by groupadd and the group exists. 

This is the output get from "#useradd -G srcds tf2"
```
useradd: user tf2 exists
```
What does this mean? "id tf2" does not show tf2 belonging to any other group other then its own. I tried also adding my user name and still get the same message. 

Running Ubuntu server 8.04

---

### Post by cyfur01 on 2009-02-26
You want to use "usermod" since, going by what you said, the user tf2 already exists and thus can't be re-created. useradd is trying to create the user tf2 and add it to your srcds group, but since tf2 already exists, it can't and fails. 

The general format is: "usermod -a -G <group1,group2...> <user>"

In your specific case:
```

usermod -a -G srcds tf2

```

---

### Post by geirha on 2009-02-26
The preferred way is to use the adduser, addgroup, deluser, delgroup commands, rather than useradd, usermod, userdel, groupadd, groupmod, groupdel. To add the user tf2 to the group srcds with adduser, do```
sudo adduser tfs srcds
```

---

