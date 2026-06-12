---
title: "/etc/skel not copying into new users"
date: 2010-03-10
forum: Desktop Environments
---

### Post by linuxgirlie on 2010-03-10
Hi,

I use to use pclinuxos and have now moved to ubuntu. I need some settings to copy down from skel and into the users home areas. I used to do this on pclinuxos by copying in the settings into /etc/skel

At the moment the settings I want are in /etc/skel but are not copying into the users home area on creation. Something is also populating the home area with folders like 'video' 'pictures' and default .gconf folders but not the ones I have placed in skel.

I also renamed skel and it still manages to copy in default settings so I know it must have these stored somewhere else.

If I manually copy the /etc/skel over my users home areas the changes come into effect, so I know it isn't a problem with /etc/skel itself.

I have tried searching but every post says to put the changes into /etc/skel and it will work.

Thanks,

Jo :p


ps. I forgot to say this is for adding a network user via pam. If I use useradd -m to create a local user then it works fine.

---

### Post by linuxgirlie on 2010-03-10
Ok I have solved the first part, it needed:

session required        /lib/security/pam_mkhomedir.so skel=/etc/skel/

pasted it in the kdm file under /etc/pam.d

Now I have to stop it telling me that it has created a home area!!

Thanks.

---

