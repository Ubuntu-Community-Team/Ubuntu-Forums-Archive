---
title: "environment variables using netbook-launcher"
date: 2010-08-02
forum: Desktop Environments
---

### Post by bakinsoda on 2010-08-02
Hi,

I'd like to set a few environment variables on my Ubuntu Netbook Remix.  On a regular Ubuntu machine, I set it in .profile since gnome reads this.  However, this is not the case in Ubuntu Netbook Remix.

Help?  Thanks

---

### Post by kerry_s on 2010-08-02
you can do /etc/environment for system wide.

are you sure .profile is not being read?

mine works i put " echo "profile read" > $HOME/test " & it worked, so it was read.

---

