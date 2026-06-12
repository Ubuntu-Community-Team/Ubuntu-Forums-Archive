---
title: "Beta Versions"
date: 2007-03-24
forum: Desktop Environments
---

### Post by Geffers on 2007-03-24
I'm still running Dapper Drake on a Dual Boot machine having been intending to upgrade but not actually getting round to it.

I see that Feisty Fawn is out as a Beta version but also know that there are a few bugs to sort out.

When does a Beta become an official 'stable' version and can one backtrack to an earlier version.

geffers

---

### Post by raja on 2007-03-24
Unless you backup an image of your existing installation, it will not be possible to rollback once you upgrade. Feisty beta was released yesterday and the final version will be released next month, so maybe you can wait till then ? I upgraded to Feisty from herd 4 (alpha) and have not had any problems. But again, I will wait another month before upgrading my pc at work.

---

### Post by Geffers on 2007-03-25
> **raja said:**
> Unless you backup an image of your existing installation, it will not be possible to rollback once you upgrade. .

Are there any utilities for backing up an image; does GParted do that? I assume it is like Windows Ghost.

Re an upgrade, I just have to save my home folder I think.

Geffers

---

### Post by jem7v on 2007-03-25
Feisty comes out officially on April 16, so it's only 3 weeks away.  It's probably worth the wait, because if you upgrade to the Beta right now you'll have to re-upgrade to the official distribution again in 3 weeks anyway (unless I'm mistaken).

Not sure if GParted will back things up, but if you edited your partition table and put your /home directory on its own partition it'll make it easier to upgrade/downgrade, because then you can just do a fresh install without affecting the things in your /home.  [http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome) for more about this.

---

### Post by iamhugeinjapan on 2007-03-25
Please note that if you plan to do an upgrade without doing a fresh install, you have to upgrade to Edgy Eft first.

Personally, with the amount of system changes between Dapper and Feisty, I would do a fresh install, but it's not required.

Rolling back to an earlier version of Ubuntu without a fresh install is one huge headache, a fresh install of Dapper would be strongly recommended.

---

### Post by orb9220 on 2007-03-25
[http://www.debianadmin.com/backup-and-restore-linux-partitions-using-partimage.html](http://www.debianadmin.com/backup-and-restore-linux-partitions-using-partimage.html)

---

### Post by Geffers on 2007-03-26
> **jem7v said:**
> Feisty comes out officially on April 16, so it's only 3 weeks away.  It's probably worth the wait, because if you upgrade to the Beta right now you'll have to re-upgrade to the official distribution again in 3 weeks anyway (unless I'm mistaken).

Not sure if GParted will back things up, but if you edited your partition table and put your /home directory on its own partition it'll make it easier to upgrade/downgrade, because then you can just do a fresh install without affecting the things in your /home.  [http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome) for more about this.

I think I am making more of a problem than I need, a reinstal is not a major task so I may well go along those lines.

Easy enough to save my home folder, re the home folder on a different partition, my initial installation was on a shared drive with an old Win98 system so I didn't compicate matters by splitting the Linux OS but now I understand a bit better may give this a try.

Thanks,

Geffers

---

### Post by Geffers on 2007-03-26
> **iamhugeinjapan said:**
> Please note that if you plan to do an upgrade without doing a fresh install, you have to upgrade to Edgy Eft first.

Personally, with the amount of system changes between Dapper and Feisty, I would do a fresh install, but it's not required.

Rolling back to an earlier version of Ubuntu without a fresh install is one huge headache, a fresh install of Dapper would be strongly recommended.

Yes I think that is sensible.

I've been away from ubuntu.com for a few months and I think the site has been altered a wee bit; they seem to refer to version numbers more that the old dapper, edgy and feisty names.

Geffers

---

