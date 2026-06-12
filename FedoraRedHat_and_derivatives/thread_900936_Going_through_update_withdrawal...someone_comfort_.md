---
title: "Going through update withdrawal...someone comfort me please!"
date: 2008-08-25
forum: Fedora/RedHat and derivatives
---

### Post by goexplode on 2008-08-25
So...here I am, sitting here, update-less ever since the [issues]("http://fedoraproject.org/wiki/FWN/Issue140") with the [Fedora/Red Hat Infrastructure]("http://forums.fedoraforum.org/showthread.php?t=197475") began. I think I'm going through withdrawals; I'm really starting to miss waking up early in the morning only to log on and have a nice list of updates waiting to be installed.

I look forward to having a nice list of updates waiting for me soon, since I know that everyone at Fedora/Red Hat is working their hardest to get everything back to normal.

So, is anyone else around here going through update withdrawals?

Perhaps we can have some sort of support group for us Fedora users who are addicted to those daily updates and suffering from withdrawals until the infrastructure is fully restored! :lolflag:

---

### Post by Antman on 2008-08-26
WHen I was running Fedora I did updates maybe once a week (if that). When I have a perfectly running system, I am more hesitant to update. :popcorn:

---

### Post by mthei on 2008-08-26
Even before this happened, I've noticed a lot less frequent updates with only about once a week (although still some of the big stuff ie SELinux policies, etc). Koji has some new builds now so I'm sure you guys will get some updates soon.
And I agree with Antman, I found I was better off disabling PackageKit and checking for updates about once a week. I used a lot less bandwidth that way.
It's a good think the Red Hat people caught on before anything bad happened. Despite what people are saying (that Red Hat are being too secretive), they had acted responsibly, even though they haven't said what exactly happened yet. Kudos to the Red Hat team.

---

### Post by goexplode on 2008-08-27
> Even before this happened, I've noticed a lot less frequent updates with only about once a week (although still some of the big stuff ie SELinux policies, etc).

Yes, I also noticed less frequent updates recently, which is fine. Perhaps the less frequent updates also somehow help in preventing me from borking my own system! :tongue:

I can be a an impatient person at times, but I think I can find patience for updates while the Red Hat people are getting everything fixed. Besides, updates really aren't that important for me anyway since nothing I do is mission critical. Installing updates all the time is me just liking the idea of being on the bleeding edge all the time with Fedora (and maybe looking for new problems to solve?). Already looking forward to Fedora 10! :popcorn:

---

### Post by Kingsley on 2008-08-28
I last updated over a week ago, so I share your pain. You can try this command if you're really desperate!

```
yum --enablerepo=updates-testing upgrade
```

---

### Post by mthei on 2008-08-28
I've been meaning to ask about this somewhere before I had found out about the fastestmirror plugin for YUM, but is there a way that we could point YUM to a specific mirror instead of it being random? It can be done in Debian-based distros and in light of the recent could-have-been disaster, it would seem like a good idea for Fedora.

---

### Post by Antman on 2008-08-29
> **mthei said:**
> I've been meaning to ask about this somewhere before I had found out about the fastestmirror plugin for YUM, but is there a way that we could point YUM to a specific mirror instead of it being random? It can be done in Debian-based distros and in light of the recent could-have-been disaster, it would seem like a good idea for Fedora.
You can edit /etc/yum.conf to point to whatever server URL you like.
```

[main]
cachedir=/var/cache/yum
keepcache=0
debuglevel=2
logfile=/var/log/yum.log
exactarch=1
obsoletes=1
gpgcheck=1
plugins=1
metadata_expire=1800
installonly_limit=2

# PUT YOUR REPOS HERE OR IN separate files named file.repo
# in /etc/yum.repos.d

[base-local]
name=Fedora $releasever - $basearch
failovermethod=priority
baseurl=http://**[COLOR="Red"]Server_of_Choice.com[/COLOR]**/yum/base/$releasever/$basearch
#mirrorlist=http://mirrors.fedoraproject.org/mirrorlist?repo=fedora-$releasever&arch=$basearch
enabled=1
gpgcheck=0

[updates-local]
name=Fedora $releasever - $basearch - Updates
failovermethod=priority
baseurl=http://**[COLOR="Red"]Server_of_Choice.com[/COLOR]**/yum/updates/$releasever/$basearch/
#mirrorlist=http://mirrors.fedoraproject.org/mirrorlist?repo=updates-released-f$releasever&arch=$basearch
enabled=1
gpgcheck=0

```

---

### Post by mthei on 2008-08-29
Thanks. I actually looked at the yum.conf after I had posted and saw that line, and then slapped myself for not realizing that sooner.

---

