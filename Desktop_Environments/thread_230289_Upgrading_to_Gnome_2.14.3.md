---
title: "Upgrading to Gnome 2.14.3"
date: 2006-08-05
forum: Desktop Environments
---

### Post by jordilin on 2006-08-05
Which packages have to be upgraded/updated to have the new Gnome 2.14.3 version?

---

### Post by Dr. Nick on 2006-08-05
It should be their by default, or after a simple system update, I have 2.14.3 in dapper and have been keeping up with the updates. I cant remember which version I had by default, but now have 2.14.3 without doing anything really special besides updates.

---

### Post by Dubbayoo on 2006-08-05
I don't see 2.14.3 in repos.

---

### Post by Dr. Nick on 2006-08-05
click the stytem menu and hit "About Gnome" That will tell you the version I have 2.14.3 but looking in synaptic a few odd packages are still at 2.14.2

---

### Post by Dubbayoo on 2006-08-05
I've only got 5 pkgs that are 2.14.3; the rest are 2.14.2.

---

### Post by ButteBlues on 2006-08-05
You can probably just get away with a simple:
$ sudo aptitude update
$ sudo aptitude dist-upgrade

That ought to install the updated Gnome packages and any dependancies.

---

### Post by jordilin on 2006-08-06
Is there no way of just selecting a few packages to upgrade Gnome 2.14.3? I don't want to upgrade the whole packages available so as to prevent issues.

---

### Post by Dr. Nick on 2006-08-07
you could try selecting specific packages in synaptic, but dependencies may make you upgrade it all of it.

Honestly I didnt even realize mine had updated, No visible changes or issues came up

---

