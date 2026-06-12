---
title: "Slow desktop environment login due to Jack audio server"
date: 2012-12-05
forum: Desktop Environments
---

### Post by stilllife on 2012-12-05
Hello, I solved this problem and I would like share the solution in the forum.
Either using xfce or gnome, the DE took about 15 seconds delay to show up. I found that was a problem related to Jack audio server (qjackctl) that I need as a startup application.

The solution was the following command:
sudo apt-get -y remove --purge qt-at-spi

that reinstall qt-at-spi so jack doesn't waste time "looking" for that

---

