---
title: "Awn 0.4.0 ppa"
date: 2009-11-06
forum: Desktop Environments
---

### Post by randomlyrandom on 2009-11-06
Hi,

Can someone please tell me where can I find AWN 0.4.0 PPAs? How to install AWN 0.4.0 in Karmic? 

Regards,
-P

---

### Post by HonoredMule on 2009-11-25
I'll second that request.  The packages are hosted in AWN's Personal Package Archive, but I can't convince Karmic to use the PPA.

I did find this page: [http://www.tuxwire.com/?p=11217]("http://www.tuxwire.com/?p=11217"), and from that I'm happy to see a new, proper process for adding the repository.  However, after adding the repo I still had no package updates.  The new method is thus and is obviously what *should* work:

```
add-apt-repository ppa:awn-testing
```

But neither using that line nor manually setting the ppa urls in /etc/apt/sources.list before running an update/dist-upgrade actually works.  apt-cache still shows 0.3.2.1-4ubuntu1 and not the PPA's 3.9.1 (which apparently is the 0.4.0 beta).

So if anyone knows hot to convince Karmic to recognize and use PPA/3rd-party repositories, I'd love to know too.


EDIT:  I found the (very stupid) problem.
1) If you have edited your sources.list/sources.list.save files, you need to revert them to stock.  Lines in those files will no longer work and actually *prevent* the files added to /etc/apt/sources.list.d/ by add-apt-repository from working as well.
2) You have to install avant-window-navigator-trunk and awn-extras-applets-trunk instead of just upgrading, even if you already have awn installed.  I can only hope that trunk doesn't really mean trunk in the traditional sense (whatever crap got auto-built from the latest broken source code).
3) Even step 2 isn't completely right, because awn-extras-applets-trunk is a referenced but non-existent package.  In its place you need to install awn-applets-c-core-trunk, awn-applets-c-extras-trunk, awn-applets-python-core-trunk, awn-applets-python-extras-trunk, and python-awn-extras-trunk.  However, it appears that just installing avant-window-navigator-trunk includes all these packages, so perhaps awn-extras-applets is getting phased out and merged into the base package.

So altogether, that's as follows (as root):
```
add-apt-repository ppa:awn-testing
apt-get update
apt-get install avant-window-navigator-trunk
```

and maybe
```
apt-get install awn-applets-c-core-trunk awn-applets-c-extras-trunk awn-applets-python-core-trunk awn-applets-python-extras-trunk python-awn-extras-trunk
```

---

