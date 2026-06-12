---
title: "xserver-xgl post-install issues"
date: 2008-02-03
forum: Desktop Effects &amp; Customization
---

### Post by mara9ato on 2008-02-03
I have installed the xserver-xgl package to enable Visual Effects and (after rebooting) it does the job, but I've got two side effects I can't get rid of:

1) My keyboard no longer works properly. It's an ABNT2 keyboard and though most keys are ok, | and \ became > and <. This is very annoying.

2) My touchpad has lost it's settings (you know, no tap to click, etc.) and the Touchpad tab in System / Preferences / Mouse is gone, so I can't adjust them again.

This behavior is the same either with the free driver or the restricted ATI driver, though the restricted driver improves video speed dramatically.

I've noticed my xorg.conf file wasn't modified by the installation of xserver-xgl, so I'm completely clueless about why the keyboard and poiting device went crazy.

In order to get my pointer and keyboard back to work I had to remove xserver-xgl and reboot.

Any help would be greatly appreciated.

Updating: I have just found these related bug entries on Launcpad:
[https://bugs.launchpad.net/ubuntu/+source/xserver-xgl/+bug/32857](https://bugs.launchpad.net/ubuntu/+source/xserver-xgl/+bug/32857)
[https://bugs.launchpad.net/ubuntu/+source/xserver-xgl/+bug/152375](https://bugs.launchpad.net/ubuntu/+source/xserver-xgl/+bug/152375)

---

