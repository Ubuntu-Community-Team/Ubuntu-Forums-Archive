---
title: "PPA for Bionic Main Doesn't Work"
date: 2018-05-13
forum: Desktop Environments
---

### Post by crabber99 on 2018-05-13
I did a fresh installation of 18.04 from the Ubuntu Download site, and it's working.

 When 18.04 was installed the Software Updater repository included this PPA:
//ppa.launchpad.net/tualatrix/ppa/ubuntu bionic main

Software Updater fails with the error message: Failed To Download Repository Information".
Details show the problem as "The repository 'https://ppa.launchpad.net/tualatrix/ppa/ubuntu bionic Release' does not have a Release file".

If I remove the PPA Software Updater runs and reports software up to date.

Is this PPA needed? What software is in this PPA that caused it to be included in 18.04? Is it safe to use, if at some point in the future it becomes operational?

Thanks

---

### Post by mc4man on 2018-05-13
Remove the ppa, there is nothing there for bionic & never will be.

---

### Post by monkeybrain20122 on 2018-05-13
Ubuntu-tweak has been dead for years. The most recent update of that ppa was 202 weeks ago, i.e almost 4 years ago,

---

### Post by tinylagarto on 2018-05-14
But if you did a fresh install that PPA should not be there in the first place. Or did you do an upgrade from a previous version?

---

### Post by deadflowr on 2018-05-14
> **tinylagarto said:**
> But if you did a fresh install that PPA should not be there in the first place. Or did you do an upgrade from a previous version?

It can happen on a fresh install on a unformatted partition.

---

### Post by monkeybrain20122 on 2018-05-14
> **deadflowr said:**
> It can happen on a fresh install on a unformatted partition.

I think a fresh install always formats the / partition. If there is a separate /home then it might not get formatted if user so chooses, but /etc/apt/sources.list is in  /.

---

### Post by mc4man on 2018-05-14
> **monkeybrain20122 said:**
> I think a fresh install always formats the / partition. If there is a separate /home then it might not get formatted if user so chooses, but /etc/apt/sources.list is in  /.
When doing a new or fresh install if one removes the previous install (the - icon) & then installs new to the exact same size & place then formatting is not auto enabled.

---

### Post by crabber99 on 2018-05-16
Thanks for the help.  I removed the PPA as suggested and all is well.

---

### Post by oldos2er on 2018-05-17
Would you please mark the thread solved? Thanks.

---

