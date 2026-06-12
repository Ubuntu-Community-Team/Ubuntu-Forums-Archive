---
title: "KDE 4.7, how to make icon which opens website in Chromium?"
date: 2011-09-10
forum: Desktop Environments
---

### Post by LolxD on 2011-09-10
Hi, i got Kubuntu 11.04 with KDE 4.7. I want to make an icon to desktop and when i click it it opens an website with Chromium, how i can do this?

---

### Post by oldos2er on 2011-09-10
Drag the Chromium icon from the Kickoff launcher to your desktop, right-click on it, choose Icon Settings, Application, change the Command: line from '/usr/bin/chromium %U' to '/usr/bin/chromium %U [http://mywebsite.com](http://mywebsite.com)' and it should work.

N.B. I'm guessing at the program location and name /usr/bin/chromium

---

