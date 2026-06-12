---
title: "RSSOwl internal browser"
date: 2009-05-10
forum: General Help
---

### Post by kaitwospirit on 2009-05-10
I've installed RSSOwl, a feed reader that I really like already. It claims to have an internal browser function, but I don't understand the instructions on how to enable this. 

Their instructions are here: [http://www.rssowl.org/help#item_13](http://www.rssowl.org/help#item_13)

Just where am I supposed to be putting in this information? Has anyone done this already that can help me out?

---

### Post by kaitwospirit on 2009-05-10
Bumping post.

---

### Post by albinootje on 2009-05-10
> **kaitwospirit said:**
> 
Their instructions are here: [http://www.rssowl.org/help#item_13](http://www.rssowl.org/help#item_13)


I just tested it, by doing this in a terminal :
```

export MOZILLA_FIVE_HOME=/usr/lib/mozilla
./RSSOwl

```
Then enabled internal browser in the settings of RSSowl, and that 
worked.
However.. also without that export line, it works! Using 2.0 Milestone 9 on Ubuntu Hardy and sun-java6-jre.

---

### Post by kaitwospirit on 2009-05-11
Looks like I just couldn't find the right setting in the preferences for awhile! Thanks, though, that DID help-sent me searching back through them again.

---

