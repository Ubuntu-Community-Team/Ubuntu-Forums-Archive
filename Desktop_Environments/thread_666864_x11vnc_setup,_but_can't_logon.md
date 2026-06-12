---
title: "x11vnc setup, but can't logon"
date: 2008-01-13
forum: Desktop Environments
---

### Post by snick512 on 2008-01-13
Hi, 

I've setup x11vnc .. and i've seem to configure it properly according to the following post


[http://www.ubuntuforums.org/showpost.php?p=771174&postcount=61](http://www.ubuntuforums.org/showpost.php?p=771174&postcount=61)


However, when i try to login from another machine, or the same machine, it says no auth; and will not continue with logging in


any help please?

---

### Post by krunge on 2008-01-14
> **snick512 said:**
> Hi, 
However, when i try to login from another machine, or the same machine, it says no auth; and will not continue with logging in


Are you certain you are using the GNOME display manager GDM as your login greeter?  The info in the post you linked to is specific to GDM and won't work for other ones (KDM, XDM, ...).

Feel free to post the contents of /var/log/x11vnc.log you collected for a failed attempt.

---

