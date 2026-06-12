---
title: "the way fix yum error missing dependency: XXXX"
date: 2008-12-16
forum: Fedora/RedHat and derivatives
---

### Post by paley_p on 2008-12-16
I am trying to update the linux by using yum:
I interrupted the update.
When i try to continue update the system:
Yum report error message as below:
error missing dependency: Perl 

this error happen because some perl PRM packetage has been install but the old verion is still on work. 
you need just remove the new version RPM packetage.

RPM -e 

I write it here and on by bloger hope can help any one.

---

### Post by taurus on 2008-12-16
Are we talking about a Fedora distro?

---

### Post by handydan918 on 2008-12-16
Sounds like you are using an RPM based distro like Fedora. You might want to look for support on their forums, or try posting [here]("http://ubuntuforums.org/forumdisplay.php?f=162")

---

### Post by Rocket2DMn on 2008-12-16
Moved to the Fedora/RedHat subforum of Other OS Talk.

---

### Post by igknighted on 2008-12-16
Give it some time.  You are probably not using the official mirror, so yours must be slow to update.  In a little try again and it should work.

---

