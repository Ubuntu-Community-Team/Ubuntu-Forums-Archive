---
title: "Do the LiveCDs get security and major bug fix updates?"
date: 2006-06-02
forum: Desktop Environments
---

### Post by dpm on 2006-06-02
Ok, my understanding is that LTS means exactly what it meant on Breezy, only for a longer time, that is, we get only **security** **updates** and **major bug fixes** for a period of 3 years.

The question is, do the LiveCD ISOs get updated as well? Or do they always remain the same and updates are only fetched upon a hard-disk installation?

Thanks.

---

### Post by aysiu on 2006-06-02
Neither live nor installer CDs get security updates.

Only installations (or live CDs in session) get updates.

If you want a CD with updates, you get the next release--Edgy, when it comes out.

---

### Post by az on 2006-06-02
[QUOTE=desp]Ok, my understanding is that LTS means exactly what it meant on Breezy, only for a longer time, that is, we get only **security** **updates** and **major bug fixes** for a period of 3 years.

The question is, do the LiveCD ISOs get updated as well? Or do they always remain the same and updates are only fetched upon a hard-disk installation?

Thanks.[/QUOTE]
There has not been any revisions to install cds in the past.  This was asked in regards to the release being supported long-term.  I think they will wait and see.  

I think if there is a need for it, they will do it.  So you would have a Dapper 6.06r1 release in that case.  There were a few discussions about this on the devel mailing list.

---

### Post by davmor2 on 2006-06-02
I think this is a debateable subject with persistance switched on would you be able to?  I personally don't know but I know with persistance you can add apps, so who knows, this maybe a point you want to ask the Ubuntu team themselves.

---

### Post by dpm on 2006-06-02
Many thanks for your replies.

[quote=azz]There has not been any revisions to install cds in the past.  This was asked in regards to the release being supported long-term.  I think they will wait and see.  

I think if there is a need for it, they will do it.  So you would have a Dapper 6.06r1 release in that case.  There were a few discussions about this on the devel mailing list.[/quote] 
This sounds promising. I hope we get to see this. 

As a particular case example, there was a bug where the firmware downloaded to my wireless network card was the wrong one, making wifi not possible on my laptop -the firmware is only loaded at bootup. This was just fixed today (i.e. after release) but I will not get to see this until the next kernel update on my hard disk installation. However, since the LiveCD does not get updates, this means I can't use a live session on this particular laptop to accesss the internet or a LAN.

In cases like this, getting 6.06r* releases would be particularly useful.

Cheers.

---

### Post by az on 2006-06-02
[QUOTE=desp] However, since the LiveCD does not get updates, this means I can't use a live session on this particular laptop to accesss the internet or a LAN.

In cases like this, getting 6.06r* releases would be particularly useful.

Cheers.[/QUOTE]

In debian's case, the change has to be quite significant.  Think huge security risk, or data loss.  If the number of updates is significant, and they are pretty well tested, you get a revision.  In some cases, the revision simply removes the package from the archive.  (Example, debian Woody shipped with cdrdao on the first cd, but it was removed in r1 and the other six revisions although it was present in Sarge (testing) at the time.)

But again, there have never been such release revisions for Ubuntu yet.

While I'm not sure, I would say don't hold your breath.

---

### Post by az on 2006-06-11
[QUOTE=azz]
While I'm not sure, I would say don't hold your breath.[/QUOTE]


It's in progress:

[https://wiki.ubuntu.com/DapperPointReleaseProcess](https://wiki.ubuntu.com/DapperPointReleaseProcess)

---

### Post by dpm on 2006-06-16
[quote=azz]It's in progress:

[https://wiki.ubuntu.com/DapperPointReleaseProcess]("https://wiki.ubuntu.com/DapperPointReleaseProcess")[/quote]

Glad to hear that.

Slightly OT, but:

1. Reading the changelogs for the last updates, it seems that (apart from the translation updates) there are lots of minor bug fix uploads. I thought that the updates system was only for major bugs. Is that right? If not, what qualifies a bug as an "update candidate"?

2. Why are most of the changelogs not yet uploaded when updates are available? The update manager simply doesn't show them. That is extremely annoying, since I have to navigate through all new changelogs in /usr/share/doc if I want to know what each particular update is about.

Cheers.

---

