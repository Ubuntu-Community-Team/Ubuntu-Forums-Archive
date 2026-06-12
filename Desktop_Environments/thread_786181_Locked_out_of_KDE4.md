---
title: "Locked out of KDE4"
date: 2008-05-07
forum: Desktop Environments
---

### Post by TeeAhr1 on 2008-05-07
wdy y'all. I guess I must have lost power this morning during an
upgrade, and now I seem to be locked out of KDE4. I get to KDM, I enter
my password, the splash screen gets about halfway through, and I am
unceremoniously dumped back to KDM.

I realized that there must have been a power outage when I came home and
my computer wasn't on; it was upon booting it that I found out that I
couldn't log in (although I got in the first time; strange...). Then I
checked aptitude and there had been an error installing libqt4-opengl. I
tried to "apt-get install libqt4-opengl --reinstall", which went through
with no errors, but didn't resolve the issue. "apt-get install -f"
claims everything is fine.

Attached is the tail end of xorg.0.log, I thought it may be relevant. I also noticed the following line in /var/log/messages that reappeared every
time I tried to log in:

May  7 19:03:05 baby-grand kernel: [ 3537.702378] klauncher[6614]:
segfault at 00000095 eip b73b3ee7 esp bfa0ee70 error 4

Aaaaand... that's all I know. Can anybody help me pinpoint this?

---

### Post by mutzinet on 2008-05-08
Your problem is maybe the same as this one: [http://ubuntuforums.org/showthread.php?p=4847868#post4847868](http://ubuntuforums.org/showthread.php?p=4847868#post4847868)

---

### Post by TeeAhr1 on 2008-05-08
Did it. Thx!

---

