---
title: "Unknown Horizions (The Game) Repository"
date: 2010-04-07
forum: Gaming &amp; Leisure
---

### Post by yedidyah on 2010-04-07
I am following the directions from the following link:

[http://www.unknown-horizons.org/site/index.php?page=download](http://www.unknown-horizons.org/site/index.php?page=download)

I am getting the following repository error when trying to install the game:

Could not download all repository indexes

The repository may no longer be available or could not be contacted because of network problems. If available an older version of the failed index will be used. Otherwise the repository will be ignored. Check your network connection and ensure the repository address in the preferences is correct.

Failed to fetch [http://packages.unknown-horizons.org/di](http://packages.unknown-horizons.org/di) ... ackages.gz 404 Not Found
Some index files failed to download, they have been ignored, or old ones used instead.

I have:
deb [http://packages.unknown-horizons.org/lucid](http://packages.unknown-horizons.org/lucid) main

I am running a 64 bit and Lucid

---

### Post by tgm4883 on 2010-05-04
This is an unknown-horizons issue. They don't have a lucid repository yet.

---

### Post by yedidyah on 2010-05-04
Well I thought so too when I first was looking into it but the instructions at
[http://www.unknown-horizons.org/site/index.php?page=download](http://www.unknown-horizons.org/site/index.php?page=download)

tell you to do this:

deb http://packages.unknown-horizons.org/$distribution release main

So I went into my browser and typed this:

[http://packages.unknown-horizons.org/lucid/](http://packages.unknown-horizons.org/lucid/)

I may be completely wrong but I put some pieces together and may have figured out that UH requires an older version of the fife gaming engine and the only one that is available to lucid is a newer version.

---

### Post by tgm4883 on 2010-05-04
So the link you went to has the weekly repo, not the release repo. The weekly repo doesn't work either though, for the fife reason you just specified

---

