---
title: "Ubuntu suddenly very slow...."
date: 2005-12-30
forum: Desktop Environments
---

### Post by putte30 on 2005-12-30
Noticed today that firefox was very slow, took like 5-10 seconds to find and load a webpage. At first I suspected my Internet connection but when I booted into my dualboot windows xp there was nothing wrong , Firefox was running smooth in xp. 

The second thing i noticed was Enemy territory. I play that game every day and today it takes about 25 second just to hit main menu but when I finally join a server everything runs just fine.

If i start a regular program like OpenOffice in runs smooth. Video and mp3 runs smooth too...

Any ideas?

---

### Post by canadianwriterman on 2005-12-30
It sounds like an issue with ipv6, although you should have been having this problem all along. Strange that it would crop up suddenly. In any event, try this:

[http://www.ubuntuforums.org/showthread.php?t=87798&highlight=ipv6](http://www.ubuntuforums.org/showthread.php?t=87798&highlight=ipv6)

You should also disable ipv6 in Firefox. In the URL line type **about:config**. In the resulting search window, type **network.dns**. Look for the reference to **ipv6 **and double click on it to change the string from false to true.

---

### Post by putte30 on 2005-12-30
Thanx mate, but the problem is still there :-(

---

