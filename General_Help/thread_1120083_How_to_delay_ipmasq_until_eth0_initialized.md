---
title: "How to delay ipmasq until eth0 initialized?"
date: 2009-04-08
forum: General Help
---

### Post by rafemonkey on 2009-04-08
A kernel update left me with broken networking. I was able to fix that problem. (See: [http://ubuntuforums.org/showthread.php?t=1118878]("http://ubuntuforums.org/showthread.php?t=1118878") ) But I am left with having to manually restart ipmasq every time I power down or restart. What I need to be able to do is delay ipmasq until after eth0 has initialized. 

There seem to be about a million (ok, really two or three) ways of organizing startup on a Linux system. I've found references to rc.d and insserv, but these don't seem to be Ubuntu standard. To make matters more complicated, ipmasq does not have a manpage, nor does it appear in the services control panel.

I've considered tacking "/etc/init.d/ipmasq restart" onto the end of rc.local, but that seems pretty kludgey, What's the correct Ubuntu way to handle this?

Thanks!

R.

---

### Post by dcstar on 2009-04-09
> **rafemonkey said:**
> A kernel update left me with broken networking. I was able to fix that problem. (See: [http://ubuntuforums.org/showthread.php?t=1118878]("http://ubuntuforums.org/showthread.php?t=1118878") ) But I am left with having to manually restart ipmasq every time I power down or restart. What I need to be able to do is delay ipmasq until after eth0 has initialized. 

There seem to be about a million (ok, really two or three) ways of organizing startup on a Linux system. I've found references to rc.d and insserv, but these don't seem to be Ubuntu standard. To make matters more complicated, ipmasq does not have a manpage, nor does it appear in the services control panel.

I've considered tacking "/etc/init.d/ipmasq restart" onto the end of rc.local, but that seems pretty kludgey, What's the correct Ubuntu way to handle this?

Thanks!

R.

All things in here are run after an interface is up:

/etc/network/if-up.d

---

