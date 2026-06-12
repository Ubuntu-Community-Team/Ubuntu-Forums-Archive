---
title: "Forced to upgrade?"
date: 2009-06-16
forum: General Help
---

### Post by cd-r80 on 2009-06-16
Looks like that Iam forced to upgrade from Intrepid to Jaunty. To get Kdenlive 7.4 to work. What is possibility that my ath5k wireless stops to work or nvidia video when upgrading. What happens to installed programs & their depencies? Like Avidemux, Moblock?

---

### Post by abhilashm86 on 2009-06-16
> **cd-r80 said:**
> Looks like that Iam forced to upgrade from Intrepid to Jaunty. To get Kdenlive 7.4 to work. What is possibility that my ath5k wireless stops to work or nvidia video when upgrading. What happens to installed programs & their depencies? Like Avidemux, Moblock?

well you can tell your software sources not to upgrade, go to 
system->administration->software sources,

there in updates tab, un-check whatever you don't want and reload, so that next time you wont upgrade...........i'm using 8.04 hardy heron this way:)

---

### Post by jre on 2009-06-19
But in the long run you will get broken, binary incompatible packages then (because they were built with older libraries, which were updated together with the main system). So I recommend you check the websites of your 3rd party repositories for the correct new sources.list entries. E.g. for moblock there are special packages for jaunty, which have the same source as the intrepid packages, but were built under jaunty.

---

