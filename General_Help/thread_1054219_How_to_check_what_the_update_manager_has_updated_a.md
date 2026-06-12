---
title: "How to check what the update manager has updated and/or rollback updates?"
date: 2009-01-29
forum: General Help
---

### Post by Jakoul on 2009-01-29
Last night there was a bunch of updates that I installed with the update manager. My problem is that one of these updates doesn't work with Steam so I can't play any games. I'm 100% sure this is the problem since the problem occured a minute or so after I updated and thanks to a Google search it has apparently happened before.

What I need to do is find out what the Update Manager updated and how to roll it back. I've already tried the Synaptic Package Manager but it's history doesn't show the Update Manager's.

Help would be much appreciated.

I'm running Ubuntu 8.10.

---

### Post by ajgreeny on 2009-01-29
Are you certain it doesn't show the updates in synaptic, because it most definitely does so in 8.04.2, which I run.  Just double check that again to make sure, as I am pretty sure it did for the short look I had at 8.10, as well.

---

### Post by mc4man on 2009-01-29
You can look in /var/log/dpkg.log

Bit hard to read thru

One way to condense lines (sure there are others

```
 ls -lrt /var/lib/dpkg/info/*.list
```

---

### Post by Jakoul on 2009-01-29
> **ajgreeny said:**
> Are you certain it doesn't show the updates in synaptic, because it most definitely does so in 8.04.2, which I run.  Just double check that again to make sure, as I am pretty sure it did for the short look I had at 8.10, as well.
Thanks for the suggestion but I've doubled checked and Synaptic's history doesn't list what the Update Manager updated for me.

> **mc4man said:**
> You can look in /var/log/dpkg.log

Bit hard to read thru

One way to condense lines (sure there are others

```
 ls -lrt /var/lib/dpkg/info/*.list
```

I just tried both of those and all they list is what Synaptic's History shows.

I know I did the update though.. It had a handful of important security updates as well as some normal updates. Any more ideas?

---

### Post by 73ckn797 on 2009-01-29
> **Jakoul said:**
> Last night there was a bunch of updates that I installed with the update manager. My problem is that one of these updates doesn't work with Steam so I can't play any games. I'm 100% sure this is the problem since the problem occured a minute or so after I updated and thanks to a Google search it has apparently happened before.

What I need to do is find out what the Update Manager updated and how to roll it back. I've already tried the Synaptic Package Manager but it's history doesn't show the Update Manager's.

Help would be much appreciated.

I'm running Ubuntu 8.10.

Nothing in the history listing updates for the day this all began? I had an issue yesterday 01/28/2009 where an Icedtea version of Java was part of an update. I do not have that loaded. That caused the Sun-Java-nonfree to begin acting up. I went into Synaptic and un-installed the Icedtea and non-free Java's then reloaded the non-free. Everything works fine again.

---

### Post by mc4man on 2009-01-29
> Any more ideas?

All packages you install from synaptic and the update manager should show in synaptic -> history. The dpkg log should show all those and manually installed packages also.

While it shouldn't matter try a reboot ...?

---

### Post by Jakoul on 2009-01-29
I tried restarting a few times and reinstalling all the of things listed in the update log. I have no idea why I didn't check earlier but all I had to do was update my video card's driver.

Sorry for making this thread and thanks for all of your's time and effort!

---

### Post by 73ckn797 on 2009-01-30
> **Jakoul said:**
> Sorry for making this thread and thanks for all of your's time and effort!

No problem at all. At least we helped you to think through the process.

---

