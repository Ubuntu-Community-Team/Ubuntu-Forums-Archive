---
title: "How to edit /etc/ufw/before.rules  file?"
date: 2009-05-15
forum: General Help
---

### Post by kewl_123 on 2009-05-15
I wanted to block ICMP echo requests. So I searched and found that I need to go in file /etc/ufw/before.rules  and comment out this line:
-A ufw-before-input -p icmp --icmp-type echo-request -j ACCEPT

I opened this file, and if I am not mistaken added a # at the beginning of this line to comment it out. Then I tried to save it but it wouldnt let me save the changes.
Can someone please tell me how do I achieve it?

Thank you.

---

### Post by Ropetin on 2009-05-15
Based on the little information give, I'm guessing you simply need the appropriate rights to change this 'system' file.  This can be acheived by using sudo;

$ sudo vi /etc/ufw/before.rules

---

