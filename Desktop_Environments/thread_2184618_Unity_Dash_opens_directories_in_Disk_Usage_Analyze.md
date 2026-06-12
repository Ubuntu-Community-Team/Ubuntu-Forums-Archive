---
title: "Unity Dash opens directories in Disk Usage Analyzer"
date: 2013-10-29
forum: Desktop Environments
---

### Post by newgiin on 2013-10-29
I'm running Ubuntu 13.10. I was trying to add programs to the launcher in ~/.local/share/applications, maybe I did something there to mess it up?

sudo apt-get purge baobab solves it, but I'd like to have my disk usage analyzer back...

woops, solution was here: [http://askubuntu.com/questions/288270/disk-usage-analyzer-replacing-nautilus](http://askubuntu.com/questions/288270/disk-usage-analyzer-replacing-nautilus)
I was just looking in ~/.local/share/applications/ instead of [FONT=Ubuntu Mono]/usr/share/applications/ for baobab.desktop[/FONT]

---

