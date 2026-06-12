---
title: "Steam won't work with new nvidia drivers"
date: 2014-12-13
forum: Gaming &amp; Leisure
---

### Post by Ed Parlette on 2014-12-13
I last used steam for linux several months ago. When I tried to use it yesterday, I got the following error message:

You are missing the following 32-bit libraries, and Steam may not run:
libnvidia-tls.so.331.20
libnvidia-glcore.so.331.20

Since the current nvidia driver version is 331.113, this is not surprising. 

Is there a fix for this, or do I have to wait for an update of the Steam For Linux software?

Thanks,
Ed Parlette

---

### Post by Drone4four on 2014-12-14
I encountered this exact error message involving steam and nvidia after updating my system yesterday.  I rebooted my system and now I can&#8217;t get to gdm.  Also now I can&#8217;t even uninstall, rollback or upgrade my nvidia drivers in my shell because I somehow borked my package tool.  I am unsure whether or not my problem is the same as your problem or if there may be some overlap.  [Here is my thread]("http://ubuntuforums.org/showthread.php?t=2256774").

---

### Post by Jamsheed_Nabi on 2014-12-19
I am also facing the same issue.

---

### Post by Drone4four on 2014-12-31
I fixed my nvidia problem.  My solution was to comment out the problematic pacakges and then run, 'sudo apt-get autoremove -f '  What this did was removed the broken packages and then upon upgrading my system, a new nvidia module was built for me kernel.  I'm not sure if this will help you two, but it worked for me.  **Ed Parlette** + **Jamsheed_Nabi** : Did you two manage to fix your nvidia package-related issues?

---

