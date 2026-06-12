---
title: "Dell Mini 1012 Won't Wake From Sleep"
date: 2010-10-12
forum: Dell Ubuntu Support (CLOSED)
---

### Post by Mark Uhde on 2010-10-12
Hi, I filed this as a bug report in Launchpad - [https://bugs.launchpad.net/ubuntu/+bug/632538](https://bugs.launchpad.net/ubuntu/+bug/632538) - but it never got any more attention than a couple of "me toos". I'm wondering if anyone here has any idea what could be causing this and what could fix it?

Machine worked great on 10.04, but won't wake from sleep fully (sounds like it's waking but screen never comes back on) on a clean install of 10.10 (didn't work on an upgrade install of 10.10 beta either...).

Thanks!

Mark

---

### Post by mikewhatever on 2010-10-12
The bug report you filed is basically invalid, since the amount of technical info it provides is next to none. What you should have done was file a bug against the **pm-utils** package as shown below.

```
ubuntu-bug pm-utils
```

The options now are to refile properly or to update the existing bug report. The latter is done as follows, where 632538 is the bug number.

```
apport-collect 632538
```

Check out the [Reporting Bugs Howto]("https://help.ubuntu.com/community/ReportingBugs?highlight=%28%28ReportingBugs%29%29") for more info.

---

### Post by Mark Uhde on 2010-10-12
Thanks Mike, I didn't do that because I wasn't SURE what package it would be a problem with. Would you mind looking to see if I updated it correctly now? Thank you!

---

### Post by bcooperb on 2010-10-15
I'll file this as a Me Too!

shutting the lid, or letting it fall asleep....goes in a comma and never wakes back up. I have to hold down the power button to turn off and back on :(

This was an Upgrade from 10.04.....which worked ok. But 10.10 has these problems mentioned

---

### Post by Mark Uhde on 2010-10-16
Make sure you put that on the bug report that it affects you too, I think the Ubuntu team is more likely to care about it if you put it there. Especially if you collect more data (following the directions I was told to a few posts up).

---

### Post by nealmcb on 2011-05-01
Launchpad bugs are the best way to follow bugs like this.  I've updated the bug indicated here, as well as the one that gave me a workaround that worked for me in Natty: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/642091](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/642091)

---

