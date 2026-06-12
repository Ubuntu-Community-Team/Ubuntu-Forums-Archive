---
title: "Replacing OpenBox with another desktop manager"
date: 2019-08-14
forum: Desktop Environments
---

### Post by sy-kalhor on 2019-08-14
Hi all. So I installed Lubuntu 19.04 64bit. Then I have installed all my packages and stuff and finally setup a nice working PC. But I just realized that my favourite terminal emulator 'guake'  can not use transparent background because of what I beleive limitation of OpenBox (please correct me if I am wrong).

I do not want to go into the process of installing another desktop (e.g. Ubuntu)...

is there a way that I replace the OpenBox with something stronger?

Or how can I add transparency support to OpenBox?

---

### Post by Dennis N on 2019-08-14
LXQt desktop is already installed in the default installation. Before logging in, use the session selector on the panel of the login screen. Select "LXQt Desktop" instead of "Openbox".

---

### Post by sy-kalhor on 2019-08-14
I just realised that I was running on LXQt already...

I went into the LQXt session settings option and enabled "Compton (X Compositor)" and after a relog I had transparency :)

---

