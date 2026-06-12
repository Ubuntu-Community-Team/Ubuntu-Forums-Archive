---
title: "Home directory for new user"
date: 2005-12-26
forum: General Help
---

### Post by rensu on 2005-12-26
I have problems with new users. Ubuntu isn't creating /home/user directory for them and problems with chmod on them. Anyone can tell me where i can conf them?

---

### Post by steve.horsley on 2005-12-26
I can't imagine what the problem might be, but you can create the directory by hand like this:```

sudo mkdir /home/newuser
sudo chown newuser:newuser /home/newuser
sudo chmod 750 /home/newuser
```

This presupposes that a group was created for the new user. The group information is stored in /etc/group in case you need to edit it, and user information is held in /etc/passwd.

---

### Post by infoseeker on 2005-12-26
I had no problems with

> sudo adduser <name>

---

