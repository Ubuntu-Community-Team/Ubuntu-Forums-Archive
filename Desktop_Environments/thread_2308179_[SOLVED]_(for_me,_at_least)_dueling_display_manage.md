---
title: "[SOLVED] (for me, at least) dueling display managers"
date: 2015-12-31
forum: Desktop Environments
---

### Post by jamesjones01 on 2015-12-31
I've been upgrading the computers at home to Ubuntu 15.10, and since my wife is used to KDE and I like having it available, I've been installing the kubuntu package after the install of plain Ubuntu. (I like having a choice.) As part of that, I'm asked whether I want sddm or lightdm to be in effect, the way that earlier on I was asked whether I wanted kdm or lightdm to run.

It appears that sddm isn't honoring that choice. At first the problem I saw was that on an HP Pavilion 15 ab135cy, with the open source AMD driver, it would boot up and after showing the lightdm login screen for a second or two, it would go blank. Closing the lid to let it hibernate and then opening it would make it possible to log in. Installing fglrx gave it away--then *both* lightdm and sddm insisted that I log in, and "ps -A | grep dm" showed them both running.

I've uninstalled sddm, and now all is well.

---

