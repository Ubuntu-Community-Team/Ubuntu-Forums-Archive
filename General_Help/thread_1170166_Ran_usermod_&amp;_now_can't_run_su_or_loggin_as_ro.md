---
title: "Ran usermod &amp; now can't run su or loggin as root. Help!"
date: 2009-05-26
forum: General Help
---

### Post by jedrollins on 2009-05-26
Ran usermod to add myself to a new group I created and now after a reboot I lost all ability to loggin as root or change to superuser. When I sudo su I get a message "user is not in sudoers file". Anybody have any suggestions. Is there a way to add me back into the su world?

---

### Post by KhurramM on 2009-05-26
try man sudoers

may be it can help u.

Or see if the root account isnt locked.

Best of luck.

---

### Post by jedrollins on 2009-05-26
No man pages on that. I tried to loggin with root and admin with no luck. I thought root was assigned the password that I login with but it's not working. I now have no ability to change any of my system. The only thing left is to start over. If anybody can help me avoid that I would be greatfull.

---

### Post by nebileix on 2009-05-26
Try restart and go into recover mode by pressing esc key during the boot menu.

From there, go into command prompt and revert/change to get ur user back.

Go check out the file /etc/group & /etc/passwd to revert back to ur own group first.

Gd luck.

---

### Post by Soul-Sing on 2009-05-26
Or recovery mode: passwd username
2x pass

Or:
-  : ```
gedit /etc/sudoers
``` or adjust with ```
visudo
```

this line is esential!:
root   ALL=(ALL) ALL
%admin ALL=(ALL) ALL

Or run: ```
echo 'root ALL=(ALL) ALL' >> /etc/sudoers
```
        ```
echo '%admin ALL=(ALL) ALL' >> /etc/sudoers
```

best luck...

---

### Post by jedrollins on 2009-05-26
Nebileix - That was it. Just went into recovery mode and edited /etc/group. Thanks for your help.

---

### Post by nebileix on 2009-05-27
No problem...

Please mark your post as [SOLVED].

Gd day..

---

