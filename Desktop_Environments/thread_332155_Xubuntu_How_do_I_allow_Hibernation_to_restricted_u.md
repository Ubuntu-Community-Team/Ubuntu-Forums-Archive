---
title: "Xubuntu: How do I allow Hibernation to restricted user?"
date: 2007-01-05
forum: Desktop Environments
---

### Post by Nopposan on 2007-01-05
O.K., I have looked around for a few days now -- perhaps I'm missing it so turn me onto it if you like.  I'm using Xubuntu 6.06 and I've installed a stand-alone web filtering system in it so that the computer's primary user, a teenager, won't be tempted to get into whatnot instead of doing homework and related internet research.  Therefore, the primary user has not been given administrative priveleges!  Yet I would like for this user to be able to use the very cool hibernation feature and also be able to shutdown the computer without typing in any password.

Is this possible to configure?  If so, then please provide instructions or a link to such instructions.

I know about creating the /libexec/whateverIdon'tremember/xfce4-shutdown-helper directory and I've done this.  Users who have administrative priveleges can shutdown and hibernate without typing a password, but the non-administrative user cannot.

Any advice you can give will be appreciated.

---

### Post by bluenova on 2007-01-05
You need to edit the sudoers file by typing:

sudo visudo

from the terminal

then add the line:

ALL ALL=(root) NOPASSWD: /sbin/shutdown

This will allow shutdown without a password. Not sure of the command for hibernation though.

---

### Post by Nopposan on 2007-01-06
Thanks, but actually I think the problem is mostly with hibernation.

What happens is that the restricted user can hibernate once, but after recovering from hibernation the user cannot shutdown or hibernate; hibernate seems to do nothing on this second try, and shutdown only logs out of xfce and lands me at the gdm screen.

---

