---
title: "High cpu usage when hoovering over dropdown menues &amp; more"
date: 2019-05-08
forum: Desktop Environments
---

### Post by tenferenzu on 2019-05-08
Hello, this is my first post here, please don't be too harsh. I already googled the issue and since I'm not on 12.04 or use an AMD CPU/GPU I'm out of ideas.

My problem:
Gnome uses up to ~50% of my CPU when just hoovering over dropdown menues like the one in the terminal. The system then laggs like crazy for .5-1 second before it opens the next dropdown column. A similar thing happens when I hoover over my panel but there CPU usage reaches up to 78%, interestingly withouth lagging as much. The problem seems to be 18.04 specific. I couldn't replicate the problem on a standard Manjaro desktop. I didn't test any other Gnome based distributions yet.

I use a Thinkpad x230, i5, 4gb RAM and a 320gb HDD.

Here a screenshot from htop to visualize the problem:

[ATTACH=CONFIG]283222[/ATTACH]


[https://imgur.com/a/9fXvFNu](https://imgur.com/a/9fXvFNu) (link if the attachment doesn't work)

Lg

---

### Post by speartip on 2019-05-08
Numerous people seem to be reporting high cpu/memory issues using Gnome-Shell. My Intel i3 system with integrated graphics, lagged & stuttered considerably. I can't help you with your issue other than to suggest using Ubuntu Budgie or Xubuntu, neither of which have that issue.

---

### Post by tenferenzu on 2019-05-10
Hello, thank you for the tip but I'd prefer Gnome.  It turned out that wayland was causing the issues. Everything works perfectly smooth on X11.  This post can be closed.

---

### Post by speartip on 2019-05-11
Not surprising. Wayland still has some quirks. Hence it's not enabled by default in 18.04.

---

