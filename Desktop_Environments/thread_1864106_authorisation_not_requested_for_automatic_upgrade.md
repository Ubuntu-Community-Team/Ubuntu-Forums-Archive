---
title: "authorisation not requested for automatic upgrade"
date: 2011-10-18
forum: Desktop Environments
---

### Post by plasmafusion on 2011-10-18
hi all.
just giving lubuntu 11.10 a try. after tiring of unity and gnome 3.
install fine. hardware fine.
after logging in, this session (fully updated via apt-get yesterday), the upgrade dialogue popped up and reported that there were 10 updates available. fine i thought. let's go. clicked to proceed but there was no prompt for my root password. the updates were just applied as if i had provided it.
if i open a terminal and issue an **apt-get update** as a regular user it throws an error.
odd.
not looking for assistance here...just reporting odd behaviour. file a bug report [here]("https://bugs.launchpad.net/lxadmin/+bug/877641")

---

### Post by mick222 on 2011-10-18
I dont think this is a bug It has been like this in oneric for a while now.
Doesn't ask when you have just logged in.

---

### Post by plasmafusion on 2011-10-18
ah..ok then...it didn't show when i searched launchpad. 
didn't happen with me when i ran ubuntu 11.10 alpha or beta either.
still say it is a bug though...regular users applying updates?
cheers.

---

### Post by mick222 on 2011-10-18
I must say I thought it was strange applying updates without using my password.I normally use either terminal or synaptic when in alpha. I thought more people would reply to this.

---

### Post by plasmafusion on 2011-10-19
same thing happened tonight.
update-manager installs updates with no password prompt. run **apt-get update** in a terminal and the correct restrictions are set...
E: Could not open lock file /var/lib/apt/lists/lock - open (13: Permission denied)
E: Unable to lock directory /var/lib/apt/lists/
E: Could not open lock file /var/lib/dpkg/lock - open (13: Permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?

---

### Post by deserthowler on 2011-10-20
I thought this was very strange too.  Just figured I'm old and just forgot that I signed in or something.

Earl

---

### Post by plasmafusion on 2011-10-21
heh :)
'senior moments' are becoming more commonplace for me too.

---

