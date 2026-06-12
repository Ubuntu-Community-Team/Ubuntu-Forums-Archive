---
title: "Request for testing of simutrans in Karmic"
date: 2010-03-15
forum: Gaming &amp; Leisure
---

### Post by slakkie on 2010-03-15
Hello all,

I've created a backport of the simutrans 102.2.1 (the version available in Lucid). However, I don't run Karmic myself so I cannot test if everything works as expected.

Could you guys help me do the testing?

PPA to add in your sources.list:

```

deb http://ppa.launchpad.net/wesleys/ppa/ubuntu karmic main 
deb-src http://ppa.launchpad.net/wesleys/ppa/ubuntu karmic main 

```

You then need to add my key to your keyring:

```

sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys D3980885DB72184B

```

Then run *sudo aptitude update* and 

```

$ apt-cache policy simutrans
simutrans:
  Installed: 102.2.1~ds1-1
  Candidate: 102.2.1~ds1-1
  Version table:
     102.2.2~ds1-1 0
        500 ftp://ftp.nl.debian.org unstable/main Packages
     102.2.1~ds1-1ubuntu-bpo1 0
        500 http://ppa.launchpad.net karmic/main Packages
 *** 102.2.1~ds1-1 0
        990 ftp://ftp.nl.debian.org testing/main Packages
        100 /var/lib/dpkg/status
     102.2.1~ds1-1 0
       -200 http://archive.ubuntu.com lucid/universe Packages
     100.0+ds1-4 0
        500 ftp://ftp.nl.debian.org lenny/main Packages

```


You should now be able to upgrade/install simutrans by running:

```

aptitude install simutrans
# or
aptitude install simutrans=102.2.1~ds1-1ubuntu-bpo1

```

Please test to see if everything works as expected. Please report your findings here or [in the backport request/bug report]("https://bugs.launchpad.net/karmic-backports/+bug/538897").

Many thanks!

---

