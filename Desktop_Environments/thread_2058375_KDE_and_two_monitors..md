---
title: "KDE and two monitors."
date: 2012-09-15
forum: Desktop Environments
---

### Post by MG&amp;TL on 2012-09-15
So, I thought I'd give KDE/Kubuntu a go. And so far, I have to say I'm impressed. Some things I'm not so happy with, like the somewhat varied default icon theme, but other than that it's pretty awesome. Kdevelop is amazing too.

Anyway. Two problems (possbly related):

1. If I login to KDE through the regular session, things crawl so badly it's unusable. After a couple of mouse clicks, it freezes entirely. The fallback environment is good, but a little jerky and sometimes fails to redraw for several seconds, resulting in mouse trails.

2. I have two monitors, one is 1024x768, and one is 1440x990. The problem is that once setup with TwinView (Separate X screen, whatever that is, fails to start), the smaller monitor has the same resolution as the larger one, resulting in cropping. How do I make it smaller?

I have an Nvidia GeForce 7300 LE, running the 173 drivers.

Any other information is freely available. :)

---

### Post by MG&amp;TL on 2012-09-15
Never mind, I fixed it.

For those with a similiar issue:

1. Get the most up-to-date drivers (nvidia-current, not nvidia-173).

2. Set them up in nvidia-settings as separate X screens, then enable Xinerama.

3. Restart X (i.e. logout and in again)

Only problem now is that the taskbar's on the wrong side, but that's not a major problem.

---

