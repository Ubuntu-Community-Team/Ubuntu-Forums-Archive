---
title: "OpenOffice ~ The application cannot be started. An internal error occurred."
date: 2005-10-18
forum: Desktop Environments
---

### Post by kevin1 on 2005-10-18
I did a fresh install of Breezy, and had been enjoying getting to know the new OO Writer. It suddenly refused to start, displaying a message window with the title:

OpenOffice.org 1.9.129

and message :  The application cannot be started. An internal error occurred.

I have since done a complete removal and re-install twice, without solving the problem. I did the same with the Java runtime. In desparation I installed OO V 1.1.5 which works fine.

I'd like to get back to the latest version because 1.1.5 does not save in .odt format.

Any ideas?

Thanks

Kevin

---

### Post by aysiu on 2005-10-18
Have you tried creating a new user and seeing if OpenOffice 2.0 works with that new user? This isn't an ultimate solution--it's just a test to see if the problem lies with the program itself or the user account.

---

### Post by kevin1 on 2005-10-19
Thanks for the reply Aysiu,

I created another user and the new OO works ok for that user.

What should I do now?

Thanks,

Kevin

---

### Post by kevin1 on 2005-10-21
I discovered that the folder /home/.openoffice.org2 had owner root, group root, and permissions = 700.
I changed so I am owner & group and permissions = 777.
Everything now works OK.
I do not know what the initial settings were, and what changed them, if they were changed.

Kevin

---

### Post by kobe008 on 2005-12-01
same problem here...
HELP!!

:confused:

---

### Post by kevin1 on 2005-12-04
Hi kobe008,

I finally solved all my problems by installing a true V2.0, as opposed to V1.9.129 masquerading as V2.0.

This thread should help:

[http://ubuntuforums.org/showthread.php?t=83535&page=3]("http://ubuntuforums.org/showthread.php?t=83535&page=3")

Good luck,

Kevin

---

### Post by Karl_jv on 2007-12-15
I had the same problem with open office 2.3, but under fedora 7. For me it was solved by removing the files in .openoffice.org2.0/user/registry/cache/

---

