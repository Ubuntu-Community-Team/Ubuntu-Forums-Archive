---
title: "Desktop crashes - Metacity segfault error 6"
date: 2011-05-05
forum: Desktop Environments
---

### Post by kazbryan on 2011-05-05
Hi guys,

Wondered if anyone can help me. I've got a ubuntu box which I use as my website development server in my office, for development and testing purposes before going to my proofing and live sites. The problem is, that since an update a few weeks ago I'm finding that the computer is randomly crashing - sometimes it's after a few minutes, sometimes after a few hours or days. I've checked the logs and it seems that there is a problem with Metacity as the following appears in the log at each crash:

karen-desktop kernel: [   68.809543] metacity[1398]: segfault at 38 ip 0805894b sp bfa3cd80 error 6 in metacity[8048000+77000]

Does this mean that there's a problem with Gnome? How do I stop this error from occuring and crashing my computer?

Thanks  in advance!

Kaz

AMD Athlon 64 Processor 3200+
512MB RAM
Ubunutu 10.4 Lucid Lynx
GNOME 2.30.2

---

### Post by kazbryan on 2011-05-08
Solved it...

Turns out that the fan on the graphics card had given up the ghost and the darn thing was getting so hot you could fry an egg on it! New graphics card installed, and all is now well again! However, I do feel like a dummy for not realising this earlier!

---

