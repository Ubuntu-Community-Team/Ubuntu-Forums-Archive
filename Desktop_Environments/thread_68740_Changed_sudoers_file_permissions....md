---
title: "Changed sudoers file permissions..."
date: 2005-09-24
forum: Desktop Environments
---

### Post by Veseliq on 2005-09-24
Hi, and sorry for the dumb problem I have...
I made the mistake to change the sudoers file permissions to 755 /default obviosly 440/ and now I can't do anything with the sudo command, it just says "sudo: /etc/sudoers is mode 0755, should be 0440" But the problem is, that I can't change the permissions if I'm not root, 'couse ofcourse I'm not the owner...  ](*,) 
How can I *fix* it...  :roll:

---

### Post by doclivingston on 2005-09-24
Restart into single user (recovery) mode, and then chmod the file. Hopefully you have physical access to the machine.

---

