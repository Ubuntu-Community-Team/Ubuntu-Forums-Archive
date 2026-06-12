---
title: "SSH and Nautilus"
date: 2006-12-08
forum: Desktop Environments
---

### Post by maino82 on 2006-12-08
I recently set up my server to accept only key-based logins for SSH and have since lost the capabilities to use SSH to transfer files in nautilus. Is there a way to set up nautilus to use keys much like you can from the command line? Or is there a separate program that would allow the same sort of file transfer capability over ssh that nautilus does that can use key-based logins? thanks!

---

### Post by UberGeekInc on 2006-12-09
Have you set ssh-add to run?  Or running something like seahorse in your sessions?   Do you have a private/public key?

If none of these made sense: 

   [http://www.cyberciti.biz/tips/ssh-public-key-based-authentication-how-to.html](http://www.cyberciti.biz/tips/ssh-public-key-based-authentication-how-to.html)

---

### Post by maino82 on 2006-12-09
I'm unfamiliar with both ssh-add and seahorse, but I'll take a look at that link and poke around the forums some more and hopefully I can get it figured out. Thanks for the ideas! I appreciate it!

---

### Post by maino82 on 2006-12-09
Just for those curious, I managed to get it working using a program called secpanel in the repositories. ssh-add and seahorse didn't take for some reason, but secpanel seems to be managing my keys nicely.

---

