---
title: "Would this sort of web browsing blocker be possible?"
date: 2009-02-13
forum: General Help
---

### Post by tneva82 on 2009-02-13
Hiya. My 7yo little brother is finally starting to get more interested in computer(and games in particular :P) and has figured that google can be used to search things(though hasn't figured out logic behind keywords. One of his queries was all games in the world(in finnish)...). Anyway this gets our mother bit worried he might stumble across something that he shouldn't do.

Anyway I thought wouldn't it be possible to monitor which web pages user is trying to look and if it's not on list of approved pages then put full stop unless user enters right password(this way it won't trouble parents). White list is lot easier than black list as there's more web pages to be blocked than there is to approve.

Is there such a program for Linux(ubuntu in particular) and if so what would their names be? Sure would make my mother relieved!

Thanks.

---

### Post by kanikilu on 2009-02-13
There have been a few threads on parental control. See if this suits your needs: [http://ubuntuforums.org/showthread.php?t=207008](http://ubuntuforums.org/showthread.php?t=207008)

---

### Post by MarblePanther on 2009-02-13
More info on Dan'sGuardian:

[http://ubuntuforums.org/showthread.php?t=436208](http://ubuntuforums.org/showthread.php?t=436208)

[https://help.ubuntu.com/community/Servers/DansGuardian](https://help.ubuntu.com/community/Servers/DansGuardian)

---

### Post by Slim Odds on 2009-02-13
Try this: [http://www.opendns.com/](http://www.opendns.com/)

---

### Post by tneva82 on 2009-02-13
Hum. OpenDNS is atleast easy to use but doesn't filter nearly enough(put the level to highest and I was still able to access finnish adult magazine's web page without any issues. Blocked Ubuntu forum however...).

DansGuardian also seems to be blacklist based...

Isn't there ANY white list based filters? One would think those would be available looking how they are pretty much THE most effective to ensure wrong pages won't be accessed...

---

### Post by FluffyElmo on 2009-02-13
Actually Dan's Guardian uses both blacklists and whitelists. For what you want you would apply what they call a "Blanket Block" which blocks everything, then add specific exceptions to the whitelist.

There may be better documentation, but this page from their wiki covers the basics. Overall, Dan's Guardian may be more complicated in some ways than the alternatives but as it's based on squid and other software you won't find anything more configurable.

[http://contentfilter.futuragts.com/wiki/doku.php?id=allowing_a_website&DokuWiki=6c7732e07358adb506415e192912cca4]("http://contentfilter.futuragts.com/wiki/doku.php?id=allowing_a_website&DokuWiki=6c7732e07358adb506415e192912cca4")

---

### Post by tneva82 on 2009-02-13
> **FluffyElmo said:**
> Actually Dan's Guardian uses both blacklists and whitelists. For what you want you would apply what they call a "Blanket Block" which blocks everything, then add specific exceptions to the whitelist.

Right. That sounds more like it! I'll definetly give it another look then.

---

