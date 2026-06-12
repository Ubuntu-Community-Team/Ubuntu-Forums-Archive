---
title: "Perhaps the Usual WINE Error?"
date: 2013-08-01
forum: Gaming &amp; Leisure
---

### Post by ceil210 on 2013-08-01
I have been to several sites and followed many tutorials, but I can't seem to get WINE installed on 12.04.  Since the logs are wicked long, I have pasted all of the ins and outs of what happens when I attempt to install wine.

---

### Post by peeteedee on 2013-08-01
Well, you might have to purge aborted Wine installs first, but...

[http://www.winehq.org/download/ubuntu](http://www.winehq.org/download/ubuntu)

---

### Post by CatKiller on 2013-08-01
This
```
W: Failed to fetch http://ppa.launchpad.net/gwibber-daily/ppa/ubuntu/dists/quantal/main/source/Sources  404  Not Found

W: Failed to fetch http://ppa.launchpad.net/gwibber-daily/ppa/ubuntu/dists/quantal/main/binary-amd64/Packages  404  Not Found

E: Some index files failed to download. They have been ignored, or old ones used instead.
```
 means there's a problem with this PPA. You'll probably want to comment that out of your sources.list while testing your new PPA.

This
```
The following packages have unmet dependencies:
 wine1.5 : Depends: wine1.6 but it is not going to be installed
E: Unable to correct problems, you have held broken packages.
```

is presumably a result of your "follow[ing] many tutorials." You'll probably need to tell us what you've actually done.

You don't need to add a PPA, though. It's in the normal repositories.

---

### Post by MikeCyber on 2013-08-02
dont use that but this:
[http://www.winehq.org/download/ubuntu](http://www.winehq.org/download/ubuntu)

---

