---
title: "Intrepid:   Powersaving Isn't Working"
date: 2009-01-24
forum: General Help
---

### Post by tbzep on 2009-01-24
After upgrading to Intrepid-64 from Hardy-64, power saving hasn't been switching off my monitor.  I really don't know what to try to troubleshoot.  I've changed settings a couple of times.  I don't have any services running that weren't running before the upgrade.  

My forum search only produced results on laptops and battery conservation. Either it's a unique problem for me, or I'm not entering the right words in the search.

---

### Post by khelben1979 on 2009-01-24
[Look here]("http://www.mail-archive.com/ubuntu-bugs@lists.ubuntu.com/msg1002463.html").

Maybe it can help? (although I realize that the event in their case might have nothing to do with your problem.)

You could report the bug [here]("https://bugs.launchpad.net/ubuntu/intrepid/+source/powersave").

---

### Post by tbzep on 2009-01-25
> **khelben1979 said:**
> [Look here]("http://www.mail-archive.com/ubuntu-bugs@lists.ubuntu.com/msg1002463.html").

Maybe it can help? (although I realize that the event in their case might have nothing to do with your problem.)

You could report the bug [here]("https://bugs.launchpad.net/ubuntu/intrepid/+source/powersave").

I'm a little hesitant on reporting it as a bug because it might be something I've screwed up to prevent it from working correctly. I've been using Ubuntu for over a year, but I still consider myself on the very low end of the knowledge scale.

I'm set up for dual boot.  I made myself boot into Vista and the monitor did turn off, so at least I know it isn't hardware related.

---

### Post by tbzep on 2009-02-04
I finally figured out the powersaving problem. It was one of those things that was too simple to realize.  **The simple solution: The powersaving feature won't turn the monitor off unless the screensaver is enabled.**  

I generally don't fool with a screensaver, so it just didn't dawn on me until I looked at my daughter's session settings, where powersaving does work correctly to turn off the monitor.

---

