---
title: "Specific RSS for kubuntu sub-forum?"
date: 2005-12-16
forum: General Help
---

### Post by jobezone on 2005-12-16
Hi! I've added an RSS feed for new posts in ubuntuforums.org, but was wondering if it's possible to do the same just for the kubuntu sub-forum(s). In konqueror indeed an RSS icon appears, but when I click and add it, it doesn't "feed" anything. This is what the feed adress is in Akregator:
EDIT:
[http://ubuntuforums.org/forumdisplay.php/external.php/external.php%3Ftype%3DRSS/external.php%3Ftype%3DRSS/external.php%3Ftype%3DRSS?type=RSS?f=99](http://ubuntuforums.org/forumdisplay.php/external.php/external.php%3Ftype%3DRSS/external.php%3Ftype%3DRSS/external.php%3Ftype%3DRSS?type=RSS?f=99)

---

### Post by GoldBuggie on 2005-12-16
Use the following format for kubuntu rss feed
```
http://ubuntuforums.org/external.php?type=rss2&forumids=99
```

If you want the subforums under the buntu section just change the forumids. 106 for desktop etc

To add more then one section just add more id's seperated by a comma. "...forumids=99,106"

---

### Post by jobezone on 2005-12-16
thanks, I now have a "kubuntuforums" feed in akregator. 
Thanks again.

---

