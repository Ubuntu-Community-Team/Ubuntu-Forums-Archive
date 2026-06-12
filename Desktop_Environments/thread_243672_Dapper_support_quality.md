---
title: "Dapper support quality"
date: 2006-08-25
forum: Desktop Environments
---

### Post by kolbi24 on 2006-08-25
I share my thoughts with you on ubuntu's support. I've been using Ubuntu for two years now, and I like it very much. Still there's one thing that disturbs me: support. Here's my story.

First I installed Dapper at home. Everything's fine, but when I try to get my TV card's remote work, I notice that the lirc-modules cannot be loaded into the kernel, dmesg contains several complaints about unknown symbols. I go on launchpad to report the bug, find that it's already reported by 2 users, first in may 20th. After my report, 3 other people confirm the bug, but there's no reply from the maintainer other than 'already fixed in upstream'. That didn't help much.

Next I install Dapper at work. Lots of documents to use, so I install kat, a KDE desktop search system. I configure it to index my home directory, and fire it up. It crashes and restarts again and again, a couple of times a second. I manage to stop it somehow, go on launchpad, find that it's already reported by a user back in may. No reply from the maintainer since.

My colleague asks me to install it on his computer. It turns out that Dapper does not recognise his simplre PS/2 keyboard. GRUB is still OK, but when the kernel boots up, the keyboard is gone. Change to USB keyboard, works fine, install Dapper, go on launchpad, report the problem. This was in early August. No reply from the maintainer since.

Is it only my observation or other people experience similar things? I use Debian too, report bugs there, and although not all of them get solved, I always receive an answer. I still prefer Ubuntu to other distributions on desktop, but it's really disturbing to report sometimes very critical bugs to /dev/null...

---

