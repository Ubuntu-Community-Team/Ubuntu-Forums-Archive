---
title: "Gnome shell tearing with intel graphics"
date: 2012-06-18
forum: Desktop Environments
---

### Post by diogojg on 2012-06-18
Hi! I've experienced a little bit of tearing on the top of the screen when watching videos. It is really anoying. I tried this solition and it go better but tearing still there:

In GNOME Shell, you can work around the bug by setting the CLUTTER_PAINT environment variable in /etc/environment:

CLUTTER_PAINT=disable-clipped-redraws:disable-culling


I'm using ubuntu gnome shell with intel graphics and my video player is VLC.

---

### Post by serwwweb on 2012-06-19
Hi. I don't have such a problem. I'm using Ubuntu gnome shell remix 12.04 with an Intel GMA950 and VLC.
Everything installed and working fine out of the box.
I do have a little problems with plain Ubuntu 12.04 with unity and gnome shell running along. That's why i installed gnome shell remix in a clean install. So far no problems and pure gnome experience without unity.
I hope this can help you.

---

### Post by sudodus on 2012-06-19
I think it is because the graphics card is not powerful enough or that the graphics driver is not efficient enough.

When I had a similar situation I found that the ultra-light desktop environment LXDE could play video much better. You can either

1. install Lubuntu on a separate small partition or

2. install LXDE into your present flavour of Ubuntu.

```
sudo apt-get install lubuntu-desktop
```
or
```
sudo apt-get install lxde
```
depending on how much you want and need.

---

### Post by serwwweb on 2012-06-20
What's the model of your graphic card?, so we can help you.

---

### Post by sudodus on 2012-06-20
> **serwwweb said:**
> What's the model of your graphic card?, so we can help you.
+1
Depending on your graphics card or chip, you might need a proprietary graphics driver.

---

