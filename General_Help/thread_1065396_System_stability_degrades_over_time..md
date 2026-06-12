---
title: "System stability degrades over time."
date: 2009-02-09
forum: General Help
---

### Post by moforilla on 2009-02-09
I have been using Linux for about a year now. I understand the basics but I am very far from an expert.

I have noticed that over a period of time from fresh install (1-3months) my system beings to crash more and more often. It becomes unresponsive, applications stall, system freezes and X crashes. The pervious few times I have experienced this problem I did not spend time investigating, I just formatted and did a fresh install.

All problems seem to disappear after a fresh install. I have done stability testing of my hardware in the past using memtest and prime95, they did not indicate any problems.

What can I do to investigate the cause of these problems?

---

### Post by cmnorton on 2009-02-14
Periodically looking through your logs is going to be part of this diagnosis. Start with 

sudo vi /var/log/syslog

Substitute your favorite editor if you do not use vi.

/var/log/messages also has valuable information in it.

Posting something about your hardware would help, as well.

---

### Post by man_bash on 2009-02-14
Windows-like garbage accumulation... Installing new distro over the old one a few times doesn't help either.

---

### Post by RJARRRPCGP on 2009-02-14
May be bad caps on the video card.

[http://badcaps.net](http://badcaps.net)

---

