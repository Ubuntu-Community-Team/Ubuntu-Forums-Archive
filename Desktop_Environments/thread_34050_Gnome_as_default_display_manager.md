---
title: "Gnome as default display manager"
date: 2005-05-13
forum: Desktop Environments
---

### Post by noerej on 2005-05-13
Hi, I've been using Ubuntu for a week now, and I've already screwed some things up. Most of it got solved by all the great howto's on this forum, but one thing remains.

I'd like Gnome to start as default desktop environment. I tried editing the /etc/X11/default-display-manager file, but to no avail. So I get a CLI at startup, and when I type xdm, I get a Debian boot splash screen and when I log in, I can access Gnome.

How do I get Gnome to start at boot again?

---

### Post by xristos on 2005-05-13
Check your /etc/rc2.d files .
There should only be SXXgdm .If there are SXXkdm or SXXxdm just rename them so they don't start with SXX . For example backupSXXkdm .

Hope I helped .

---

### Post by shakin on 2005-05-13
[QUOTE=xristos]Check your /etc/rc2.d files .
There should only be SXXgdm .If there are SXXkdm or SXXxdm just rename them so they don't start with SXX . For example backupSXXkdm .

Hope I helped .[/QUOTE]

```

$ sudo dpkg-reconfigure gdm

```

Should also do the trick.

---

### Post by noerej on 2005-05-13
Yeah, I just had to reinstall gdm via apt-get.
Thanks for the quick replies!

---

### Post by dougmorin on 2008-06-08
Just an addition to this thread.... I renamed in the /etc/rc2.d directory my S50kdm to backupS50kdm and also ran the sudo dpkg-reconfigure gdm and it worked for me.

background: I installed ubuntu and then install the kubuntu-desktop and was using kdm for a while and decided after upgrading to ubuntu 8.04 that i wanted to try out gnome again.  I was able to restart in gnome but I did not have any of the gnome specific functionality, so that is where i left off.

---

