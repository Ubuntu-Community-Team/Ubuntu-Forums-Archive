---
title: "How to remove unsupported packages?"
date: 2009-01-03
forum: General Help
---

### Post by Quaxo76 on 2009-01-03
Hello all,
In an attempt to fix some problems I was having, I enabled the proposed and backports repositories (unsupported), thinking that maybe a more "bleeding edge" version of the softwares might solve my problems.

It didn't.
It upgraded 78 packages (including a new kernel), but I still had my problems. And after that, I find my system much less stable. I had a couple of total freezes (frozen mouse, dead keyboard) and issues with sound and networking. I also get sudden and unexplained "pastings" of text. While I was writing this, suddenly the text "[ RIGHT ] [ /RIGHT ]" appeared in the middle of what I was writing... ?!?
So I would like to roll back to the stable, supported versions of the packages. I unchecked the "unstable" repos, and reloaded the packages list... but nothing changed. No package was "down-graded". 
How do I tell my system that I want to get back to the official versions of the packages? I have no idea which packages have been upgraded, so I can't do that by hand...

Thank you,
Cristian

---

### Post by drs305 on 2009-01-03
Good and bad news. The good news is that changes made by ubuntu's package manager are logged in /var/log/dpkg.log  The bad news is that you will probably have to manually go through a lot of entries. If you know the time you installed the updates it will help things out but still won't tell you which ones came from which repository.

---

### Post by Quaxo76 on 2009-01-03
Oh gosh. I activated the repos 5-6 days ago. But after that I installed some "official" software that I want to keep. I was hoping that the system would realize that the installed version of a given package doesn't match what resides in the "authorized" repositories... and act consequently, downgrading the package... :(
And anyway, even when I find out which packages I have to downgrade, how do I do? Do I have to uninstall them, then clear the apt cache and reinstall?

---

### Post by drs305 on 2009-01-03
Once (and if) you have identified a package that is a later version than you want, you can highlight it in synaptic and then from the top menu select Package, Force Version. If there is another version available, you will be able to select it.

Since you said you upgraded a large number of packages 5-6 days ago, you can probably check the date/times to find out when that was, as there will be many more entries at that point than during normal updates. A small consolation, I know...

---

