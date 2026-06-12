---
title: "Fresh Kubuntu install; KDE extremely sluggish"
date: 2009-05-02
forum: Desktop Environments
---

### Post by crisnoh on 2009-05-02
Just did a clean install of Kubuntu 9.04 yesterday.  I've turned compositing off and still with only a couple windows open (firefox and kontact) KDE is very slow.  Is this a problem anyone else has had and been able to resolve.  Can anyone tell me what I can adjust to get things a bit snappier?

---

### Post by Arup on 2009-05-02
Install your video drivers, in case of nvidia or ATI, get them from the manufacturer's site.

---

### Post by crisnoh on 2009-05-02
Yeah, should have mentioned.  I'm using an Intel graphics card.

---

### Post by crisnoh on 2009-05-02
Looks like I jumped on the forums a bit too quickly, but maybe this will help someone else out.  It looks like there's an issue with Intel cards and either the latest kernel version or the latest version of X.  I'm not entirely clear on where the issue lies.  The following portion of the 9.04 release notes helped me work around the issue.

[_Performance regressions on Intel graphics cards_]("http://www.ubuntu.com/getubuntu/releasenotes/904#Performance%20regressions%20on%20Intel%20graphics%20cards")

Essentially, adding the following to the Device section of my xorg.conf providing significant performance improvements:

```
        Option          "AccelMethod" "UXA"
        Option          "MigrationHeuristic" "greedy"
```

---

