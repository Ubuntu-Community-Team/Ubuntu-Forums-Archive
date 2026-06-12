---
title: "Security? Full access to Windows partition!"
date: 2009-02-02
forum: General Help
---

### Post by bartenst on 2009-02-02
Hello!

I have successfully installed Ubuntu 8.10 via Wubi on all Windows XP computers at school. When I boot up Ubuntu even the regular users are able to write to the Windows partition (/host). How can I prevent regular users (non root) from writing to the Windows partition?

Thanks a lot in advance,
Dominik

---

### Post by brandon88tube on 2009-02-02
Have you tried changing the permissions of the /host folder?

EDIT: Also, did you make new accounts with limited privileges? I would suggest doing this and then change the /host folder permissions to not allow the new limited accounts to view or create/delete files.

---

### Post by bartenst on 2009-02-05
brandon88tube, thanks for your reply! Can I just do a "chmod -R 755 /host" without affecting the permissions set in Windows?

Thanks for your reply!
Dominik

---

### Post by jchiar on 2009-02-05
I assume there are win boxes on that network also, so I looked at DanniWeb and found:
[http://www.daniweb.com/forums/thread9333.html](http://www.daniweb.com/forums/thread9333.html)
There is also a GUI in Hardy/Intredpid where one can set User Permissions.
System>Administration>Users and Groups, unlock it.
Then select whatever authorizations>select or de-select any permissions that might be an invalid argument.
Of course the terminal is the suggested way to do these things, and the answer previously given was a solution.

---

### Post by brandon88tube on 2009-02-05
> **bartenst said:**
> brandon88tube, thanks for your reply! Can I just do a "chmod -R 755 /host" without affecting the permissions set in Windows?

Thanks for your reply!
Dominik

I would think so, but I am not entirely sure as I have never done this myself.

---

