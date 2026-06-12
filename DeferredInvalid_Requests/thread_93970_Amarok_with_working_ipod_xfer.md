---
title: "Amarok with working ipod xfer"
date: 2005-11-23
forum: Deferred/Invalid Requests
---

### Post by anders.ostling on 2005-11-23
I would really love to see an Amarok version where the iPod transfer really works. 1.3.1-1.3.5 seems broken with various ipod defects. Otherwise, this is the best music app ever built on Linux! Keep it up.

So my request is for the 1.3.6, or even 1.4 (b) release of Amarok.

---

### Post by 23meg on 2005-11-23
Ipod transfers do work with 1.3.1 - 1.3.5 for most people. Please open a problem thread in the appropriate section if this isn't the case for you, stating your Amarok version, ipod model and the exact errors you get.

And please be more careful when requesting a backport; your title doesn't indicate the version you request, there's already a request in this forum for 1.3.6, and 1.4 isn't in Dapper yet.

---

### Post by anders.ostling on 2005-11-23
[QUOTE=23meg]Ipod transfers do work with 1.3.1 - 1.3.5 for most people. Please open a problem thread in the appropriate section if this isn't the case for you, stating your Amarok version, ipod model and the exact errors you get.

[/QUOTE]
These problems has been reported by me and several others during the last month(s) in bugzilla, and the developer has acknowledeged the "bug" and told us that it is fixed in the upstream (post 1.3.5) release, but that there were too many things that could break if he released 1.3.6 in Breezy.

> 
And please be more careful when requesting a backport; your title doesn't indicate the version you request, there's already a request in this forum for 1.3.6, and 1.4 isn't in Dapper yet.


I dont want to be rude, but I dont request _any_ specific version, just a version that the developer has faith in :-) and that is bealived to work with ipod transfers. It may be 1.3.6.

Thanks anyway for your energy in this question :-)

Anders

---

### Post by 23meg on 2005-11-23
Please read [the policy on requesting backports]("http://www.ubuntuforums.org/showthread.php?t=40291") if you haven't; you're supposed to only request apps that are already in Dapper. And stating a specific version in the title makes jdong's job a little easier; it's the convention, thus my little reminder. 

There seems to be no all-encompassing ipod issue with 1.3.1 or 1.3.5; I have had transfers working fine in both, with an ipod mini and a 20gb ipod. So there isn't really a single thing as "a version of Amarok with working ipod transfers"; transfers have been working fine for me ever since I started using Amarok, if that's any reference. It's likely that the problems are specific to your hardware, which is why I suggested opening a problem thread.

And if the developer stated that many things could break, a backport is quite unlikely. Sorry if all this sounds too negative; it's not meant to.

---

### Post by anders.ostling on 2005-11-23
> **23meg]Please read [the policy on requesting backports]("http://www.ubuntuforums.org/showthread.php?t=40291") if you haven't said:**
> 

Have not, will do :-).

> 
There seems to be no all-encompassing ipod issue with 1.3.1 or 1.3.5; I have had transfers working fine in both, with an ipod mini and a 20gb ipod. So there isn't really a single thing as "a version of Amarok with working ipod transfers"; transfers have been working fine for me ever since I started using Amarok, if that's any reference. It's likely that the problems are specific to your hardware, which is why I suggested opening a problem thread.

Bug 16375, filed in september. It involves 1.3.1 and iPod mini 4GB, latest generation. KDE developers claims that it is fixed in 1.3.3, others say 1.3.6. Oh well. I just wanted to be able to xfer files to my pod w/out resorting to Windows. Silly me.

[QUOTE]
And if the developer stated that many things could break, a backport is quite unlikely. Sorry if all this sounds too negative; it's not meant to.

No problema. I guess I just have to wait for this to be fixed in the future.
Anders

---

### Post by 23meg on 2005-11-23
[QUOTE=anders.ostling]
Bug 16375, filed in september. It involves 1.3.1 and iPod mini 4GB, latest generation. KDE developers claims that it is fixed in 1.3.3, others say 1.3.6. Oh well. I just wanted to be able to xfer files to my pod w/out resorting to Windows. Silly me.
[/QUOTE]
I still think you should do a forum + wiki search and if you can't find a solution, post a problem thread. Maybe the problem is specific to your configuration in some way and others on the forum have found a fix / workaround. My 2nd gen mini has worked with every version since 1.3.1.

---

### Post by jdong on 2005-11-23
Talked to KUbuntu folks for you, and they're considering releasing breezy-updates for it since we can't Backport it (libtunepimp2 too old)

---

### Post by celian on 2005-11-28
Not sure which problem you're having with your iPod transfers, but if they're anything similar to mine, then look here:

[http://bugs.kde.org/show_bug.cgi?id=115506](http://bugs.kde.org/show_bug.cgi?id=115506)

That states that these problems will only be fixed with the inclusion of libgpod in the program to replace their own custom ipod functions. This to take place in 1.4 release.

- Celian

---

