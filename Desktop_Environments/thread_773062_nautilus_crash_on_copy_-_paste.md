---
title: "nautilus crash on copy - paste"
date: 2008-04-28
forum: Desktop Environments
---

### Post by eliabramo on 2008-04-28
I've upgrade from 7.10 to 8.04 and I have two problems:

1. When I copy and paste some files form one nautilus window to another, sometimes nautilus crashes. It doesn't crash when I drag and drop the files.
Important - it happens only when I log in with Hebrew local. It doesn't crash on English local.

2. I can't reach the panel properties on right click on the panel. It seems that some of the options (panel properties, move\delete\add applets) are blocked.

I've upgrade through the update manager.

---

### Post by asiersar on 2008-04-30
I am experiencing your first issue, but with the Basque locale. It only happens when I drag and drop (and sometimes when I copy&paste) files from and to directories that were renamed when I switched from English locale to Basque locale. For example, if I drag a file to the desktop. In the English version the desktop contents are stored in a folder called "Desktop" in my home directory. When switching to Basque, the desktop contents are stored in a new folder called "Mahaigaina" (desktop in Basque). It seems that Nautilus (in fact, I think it is gvfs) doesn't recognize this change.

---

### Post by asiersar on 2008-04-30
I filed a bug report on this issue in Launchpad:

[https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/224943](https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/224943)

---

### Post by agibby5 on 2008-04-30
I'm also experiencing the first problem...

---

### Post by asiersar on 2008-05-01
OK, this is a known problem of some localization packages:

[https://bugs.launchpad.net/ubuntu/+source/language-pack-gnome-es/+bug/197224](https://bugs.launchpad.net/ubuntu/+source/language-pack-gnome-es/+bug/197224)

It will be solved when the packages are updated in HH.

---

### Post by djcrash1981 on 2008-05-08
Someone know when this problem is going to be solved??? 
Because I'm experience the same problem when i try to copy and paste a folder with files inside.

I'm using Hardy on Spanish locale.

What happened to ubuntu, it was so nice and stable, and now it have a lot of bugs :S specially with nautilus.

---

### Post by asiersar on 2008-07-22
I managed to solve the problem using a dirty workaround. I just replaced the defective "nautilus.mo" file in my /usr/share/locale-langpack/eu/LC_MESSAGES folder with the old version used in Ubuntu Gutsy.

In my case (Basque locale), I got the old package here:
[http://security.ubuntu.com/ubuntu/pool/main/l/language-pack-gnome-eu-base/language-pack-gnome-eu-base_7.10+20080205_all.deb](http://security.ubuntu.com/ubuntu/pool/main/l/language-pack-gnome-eu-base/language-pack-gnome-eu-base_7.10+20080205_all.deb)

Then I unzipped it, unzipped "data.ta.bz2", got nautilus.mo file and copied it to /usr/share/locale-langpack/eu/LC_MESSAGES

I hope this will help. But hey, if it doesn't work, don't blame me! :KS

---

### Post by stuckoverflow on 2008-08-08
Hey! it worked like a charm!!

Thanx

---

