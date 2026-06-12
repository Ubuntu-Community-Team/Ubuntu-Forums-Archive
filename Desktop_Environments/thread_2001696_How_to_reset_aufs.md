---
title: "How to reset aufs?"
date: 2012-06-11
forum: Desktop Environments
---

### Post by Magellan1186 on 2012-06-11
Hello everyone!

I've installed Xubuntu 12.04 with aufs, merging my 3 physical drives into one logical. Some time ago it looks like aufs got corrupted, not properly showing me properly the merged content and reporting of having 16.0 EiB free out of 4.1 TiB. So, it looks like aufs needs to have a kind of full database reset for further re-mount. Unfortunately I didn't manage to find any information in internet how to do this. Uninstallation of aufs-tools with "--purge" key and re-installation doesn't help.
Could you please help with the solution?

Thank you in advance.
My best regards / Ilya.

---

### Post by Magellan1186 on 2012-06-12
Actually the issue is solved with help of aufs author.
But there is another issue. I was suggested to install newest version of aufs according to: [http://aufs.sourceforge.net/](http://aufs.sourceforge.net/). And got really stuck with even first step:
patch -p1 < ~/aufs3-standalone.git/aufs3-base.patch
 can't find file to patch at input line 7
 Perhaps you used the wrong -p or --strip option?
 The text leading up to this was:
 --------------------------
 |aufs3.0 base patch
 |
 |diff --git a/fs/namei.c b/fs/namei.c
 |index 14ab8d3..eb4aef1 100644
 |--- a/fs/namei.c
 |+++ b/fs/namei.c
 --------------------------
 File to patch:

So, the question: is there any possibility to update a package which is being delivered within "apt-get install aufs-tools" in easier way than to update kernel and make compilation of the package?

Thanks.

---

