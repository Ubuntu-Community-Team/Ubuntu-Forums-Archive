---
title: "How to reset the user profile after every logoff?"
date: 2011-11-06
forum: Desktop Environments
---

### Post by news_js on 2011-11-06
Hi!

How to reset the user profile after every logoff? Sabayon no longer works. The purpose is to allow the use of Ubuntu in a public school library, so the new user will have always a clean profile. Thanks.

---

### Post by Lars Noodén on 2011-11-06
Once you have the settings the way you like them you can copy the whole directory to another location.  

You can use rsync with the --delete option to copy from that location to the user directory.  I'm not sure if you can do that every after every logoff but you should certainly be able to do that after every log in.  rsync only deals with the changes so it should be quite fast.

---

### Post by news_js on 2011-11-06
Hi!

Until now I did this:

**sudo mkdir /home/backup**

**cp -r -p /home/user/ /home/backup** (-p to preserve user ownership)

Now I have: **/home/backup/user**

Concerning the Rsync I thought about this command:

**rsync -q -r --delete /home/backup/user/ /home/user/**

Is this ok?

Where do I put this command? In ".profile"?

But I have a problem: user can delete files on /home/backup/home/

I'm confused about ownership. Was I correct when I initially did: "cp -r **-p** /home/user/ /home/backup"? Without the "-p" argument the owner would be root instead of user.

Thanks and regards.

---

