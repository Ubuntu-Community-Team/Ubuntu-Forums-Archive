---
title: "Compiz-plugins ??"
date: 2006-09-30
forum: Desktop Environments
---

### Post by gorded on 2006-09-30
For the past week when i do a dist-upgrade compiz-plugins is held back becuase a compatible compiz-core is not aviable. Have they stop adding to compiz or what?

These are the repositories i am using for compiz

#compiz Quinn's
deb [http://www.beerorkid.com/compiz](http://www.beerorkid.com/compiz) dapper main
deb [http://xgl.compiz.info/](http://xgl.compiz.info/) dapper main
deb-src [http://xgl.compiz.info/](http://xgl.compiz.info/) dapper main

and this is what i get when i try to install compiz-plugin directly with apt-get.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help resolve the situation:

The following packages have unmet dependencies:
  compiz-plugins: Depends: compiz-core (>= 0.0.13.54) but 0.0.13.52-0ubuntu1 is to be installed[/CENTER][/CENTER]

I'm not worried or anything it just seem a bit strange for an upgrade like this to take such a long time. I just wondering if anyone else is experiencing the same thing

Thanks

---

### Post by infol on 2006-09-30
Have you tried ```
sudo apt-get --reinstall compiz-core
```

As far as I know the latest version should still be in the repo's (but the latest update is just about a week old)..

---

### Post by gorded on 2006-09-30
sudo apt-get --reinstall compiz-core
E: Invalid operation compiz-core


it doesn't work

---

### Post by astoltz on 2006-09-30
Quinn's version of compiz has been forked and is now called Beryl.  

The HowTo is [here]("http://www.ubuntuforums.org/showthread.php?t=268036")

and the announcement from Quinn is [here]("http://forum.beryl-project.org/topic-4591-beryl-informations-announcement")

---

