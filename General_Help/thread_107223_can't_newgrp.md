---
title: "can't newgrp"
date: 2005-12-22
forum: General Help
---

### Post by avc on 2005-12-22
I can't get newgrp to work.

1. First I created a group with "sudo groupadd joepublic".
2. Then I edited /etc/group, adding my user to the line: "joepublic:x:1002:avc".
3. I logged off avc and logged back on.
4. I type "newgrp joepublic", and it asks me for a password.

According to "man newgrp", I shouldn't be asked for a password since I am a member of the group. I verify this by typing "groups" and getting "avc adm dialout cdrom floppy audio dip video plugdev lpadmin scanner joepublic". I put in my password, and it doesn't work (as it shouldn't). I try "newgrp video", and it works without a password, suggesting that there's something wrong with the group I created. What's wrong?

---

### Post by ape on 2005-12-22
You also need to modify the /etc/gshadow file to add your user account to the group there.

---

### Post by avc on 2005-12-22
Thanks. That works. Also I discovered the easy way to do it is gpasswd -a <user> <group>. Handles both /etc/gshadow and /etc/group.

---

