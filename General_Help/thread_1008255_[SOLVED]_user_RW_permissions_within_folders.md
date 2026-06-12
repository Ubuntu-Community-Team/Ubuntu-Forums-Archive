---
title: "[SOLVED] user R/W permissions within folders"
date: 2008-12-11
forum: General Help
---

### Post by melbs on 2008-12-11
Hi all,

I am working with the software, Moodle, on our Linux server running Ubuntu at work. I need permissions to read and write in that Moodle site folder. I was given permissions and it works in the MAIN folder but when I go in any folder I do not have those permissions. What does my network guy have to type in for me to have those permissions? (I'm very new to Linux and so is the network guy..)

Thanks!

---

### Post by taurus on 2008-12-11
Your IT administrator guy needs to change the permissions, chmod, in all the subdirectories to read/write so you can write to them.

What is the location of that main directory (complete path) and who owns it?

```
ls -la <that main directory>
```

---

### Post by melbs on 2008-12-11
/usr/share/moodle

moodle-admin owns moodle and I am a member of moodle-admin.

---

### Post by taurus on 2008-12-11
You can change permissions of /usr/share/moodle and anything under it to read/write/executable for owner and group.

```
sudo chmod -R 775 /usr/share/moodle
ls -la /usr/share/moodle
```

---

### Post by melbs on 2008-12-11
How/where does he specify which group/user has those permissions?

---

### Post by taurus on 2008-12-11
He can specify moodle-admin to be both owner and group (if there is such a user--moodle-admin--in /etc/passwd & /etc/group) of /usr/share/moodle and everything under it.

```
sudo chown -R moodle-admin:moodle-admin /usr/share/moodle
ls -la /usr/share/moodle
```

---

### Post by melbs on 2008-12-11
Thanks we will give it a try.

---

### Post by melbs on 2009-01-21
> **taurus said:**
> He can specify moodle-admin to be both owner and group (if there is such a user--moodle-admin--in /etc/passwd & /etc/group) of /usr/share/moodle and everything under it.

```
sudo chown -R moodle-admin:moodle-admin /usr/share/moodle
ls -la /usr/share/moodle
```


This is from awhile back - but I do not log in as moodle-admin I got in with a different username. However, I am in the moodle-admin group. Would the above code work even if it does not set me as owner since moodle-admin is the group and I am apart of that group? Thanks.

---

