---
title: "Where'd my space go...?"
date: 2009-02-06
forum: Desktop Environments
---

### Post by Pablo Pablovski on 2009-02-06
OK, so I installed Jaunty in a Virtualbox guest VM (with Intrepid as VM host), and as I was doing it I noticed the space on my root partition, which isn't used to store Virtual machine VDIs / snapshots, slowly reducing. 

Once the Jaunty VM install finished, the incremental reduction in space halted, but it didn't get released - in all, looks like around 250MB of space has "disappeared".

I have /root and /home on the same disk (I know, I know...) and Virtualbox is set to create its VDIs and snapshots on a separate physical disk - I've checked and all's present and correct there. 

I rebooted to check if maybe the space was being taken up by a temporary Virtualbox cache, but after boot, it's still reduced compared to what it was before installing Jaunty.

So, what could be taking up the space? Or, how can I find out what files have been created / expanded today?

TYVM in advance...
PP

---

### Post by Pablo Pablovski on 2009-02-07
Tricky, uh? :D

---

### Post by HavocXphere on 2009-02-07
Install filelight. Graphic display of where the space goes.

Only problem with that is that it looks at /media/ too. (700gb of stuff there...takes forever).

---

### Post by Pablo Pablovski on 2009-02-07
Thanks for that. Looking at filelight now.. It's amazing how much stuff builds up over the years - my GoogleEarth cache is over 2GB! :D

---

