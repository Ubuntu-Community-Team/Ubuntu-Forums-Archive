---
title: "KDE 4.10 in Kubuntu 12.04"
date: 2013-04-17
forum: Desktop Environments
---

### Post by c2tarun on 2013-04-17
Hi friends,

I googled and found that to install KDE 4.10 we have to add kubuntu-backport repository and then it'll update to KDE 4.10. Problem is it is updating lot more packages then just KDE. Will KDE 4.10 update will ever be included in main repositories of Kubuntu 12.04? If yes then any idea when?

---

### Post by ronnoc on 2013-04-18
My guess would be that it will only be available via the backports PPA. Is there a reason that you do not wish to have other packages updated as well?

---

### Post by c2tarun on 2013-04-19
> **ronnoc said:**
> My guess would be that it will only be available via the backports PPA. Is there a reason that you do not wish to have other packages updated as well?

I read somewhere that backport packages are not as stable as main packages. And I am planning to run Kubunu 12.04 for long time, so stability is required.

---

### Post by orb9220 on 2013-04-19
That's a generalization and not so accurate. As have seen main updates break things just as much as PPA's. Depends on what's being updated. And who the PPA's are from. Some 3rd party single project thing can be problematic if the dev isn't keeping up. But main PPA's have been trouble free for me.

But as to KDE started with 4.9.4 it had a couple of performance issues. But backported 4.10 and runs even faster and smoother than 4.9.4 did. Also updating to 4.10.1 and then 4.10.2 was without any issues and updates where mostly bug fixes which is always appreciated.
.

---

### Post by c2tarun on 2013-04-19
> **orb9220 said:**
> That's a generalization and not so accurate. As have seen main updates break things just as much as PPA's. Depends on what's being updated. And who the PPA's are from. Some 3rd party single project thing can be problematic if the dev isn't keeping up. But main PPA's have been trouble free for me.

But as to KDE started with 4.9.4 it had a couple of performance issues. But backported 4.10 and runs even faster and smoother than 4.9.4 did. Also updating to 4.10.1 and then 4.10.2 was without any issues and updates where mostly bug fixes which is always appreciated.
.

Ok,. In case anything went wrong after updating how can I revert?

---

### Post by Aide9aic on 2013-04-20
> **c2tarun said:**
> Ok,. In case anything went wrong after updating how can I revert?
You could install the **ppa-purge** package:
```
sudo apt-get install ppa-purge
```

Then add the Kubuntu backports PPA and perform a **dist-upgrade**. If things go south for you, you can revert:
```
sudo ppa-purge ppa:kubuntu-ppa/backports
```

That said, many of our members at Kubuntu Forums are running with the backported KDE SC 4.10 and it's working quite well. Our backported packages are maintained by the same folks who build all of Kubuntu.

---

### Post by c2tarun on 2013-04-22
> **steveriley said:**
> You could install the **ppa-purge** package:
```
sudo apt-get install ppa-purge
```

Then add the Kubuntu backports PPA and perform a **dist-upgrade**. If things go south for you, you can revert:
```
sudo ppa-purge ppa:kubuntu-ppa/backports
```

That said, many of our members at Kubuntu Forums are running with the backported KDE SC 4.10 and it's working quite well. Our backported packages are maintained by the same folks who build all of Kubuntu.


I installed KDE 4.10 and man its a charm. Though I heard pretty good reviews of Ubuntu 13.04 from "The Linux action show", but still I am thinking of delaying installing Ubuntu 13.04 just because latest KDE is sooooooooooooooooo nice :)

---

