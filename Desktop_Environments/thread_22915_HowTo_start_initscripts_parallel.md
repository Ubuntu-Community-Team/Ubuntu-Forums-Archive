---
title: "HowTo start initscripts parallel"
date: 2005-03-30
forum: Desktop Environments
---

### Post by banishedknight on 2005-03-30
Hello,

how can I configure Ubutunu to start init scripts with the same number (e.g. /etc/rc2.d/S05*) parallel at bootup?
This can lead to a much faster bootup than excute every script one after another.

Sometimes it's just nerving to see the systems stopping for 5 seconds just to search for a dhcp adress. 

Thx

P.S.: I think Solaris10, RH and Gentoo can do this, but not sure.

-----
Edit

Sorry to place a question in the HowTo section, I tried it first in "Forum ApplicationSupport" but got no answer  :(

---

### Post by TravisNewman on 2005-03-30
No questions allowed in the howtos. Sorry! If you put it in Forum Support, that's for Forum questions only. Moving to the appropriate section, so hopefully someone will know there.

---

### Post by mrincredible on 2008-05-03
Simplest:

[https://answers.launchpad.net/ubuntu/+question/4763](https://answers.launchpad.net/ubuntu/+question/4763)

in /etc/init.d/rc, add:
```
CONCURRENCY=shell 

```

Other links:
[http://www.linux.com/articles/53613](http://www.linux.com/articles/53613)

[B]PS
[/B] I thought forum staff were there to help people. The previous post is most unhelpful, specially as this page pops up #1 on Google when searching for "ubuntu parralel bootup".

Why not just post a link labelled "thread moved _here_"? Were you bullied as a child, and now you're stabbing back at the world, Mr. Thumb? :lolflag:

---

