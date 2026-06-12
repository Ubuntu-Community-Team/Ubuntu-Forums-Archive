---
title: "emacs makes gnome freeze"
date: 2009-02-20
forum: Desktop Environments
---

### Post by rgrig on 2009-02-20
I didn't use emacs for some time, probably for a few upgrades. I realized that now when I open it it works just fine until I try to switch focus away (e.g., ALT-TAB, click on a different workspace, etc.) When I do that, gnome (or X?) freezes for about 20s. During that time all I can do is switch to the terminal (e.g., CTRL-ALT-F1). In 'top' nothing looks suspicious: no CPU or memory hog.

The following emacs* packages are installed:
emacs,
emacsen-common,
emacs-goodies-el,
emacs22,
emacs22-bin-common,
emacs22-common,
emacs22-gtk,
emacsen-common.

---

### Post by robsol on 2009-03-23
I a a newbie to Ubuntu, having just installed 8.10 on a Toshiba Portege R600 after getting fed-up with Macs and MacOS,  But I used Debian before MacOS and hoped to quickly get back to work in true linux.

OOPS - Emacs freezes up the whole computer  at CNTRL or SHIFT or ALT key combinations that should operate the workspace switcher.  Some times the computer revives by itself after a long wait but more often I have to suspend and restart.

I guess it should be possible to delete those combinations out of the emacs system but don't know how.

I installed xemacs which does not have this problem but it has too lousy fonts for me to work with.

I am now in desparation trying to find out how these forum threads work, not too clear.  This message is  in answer to a pertinent one  with the same complaint that I found but it seems it was never answered.   Seems to me this is a serious bug.  How does one go about for such?

Rob

---

### Post by avilella on 2009-04-30
Hi,

If you haven't solved the problem by updating to 9.04, can you replicate the problem and create a bug report at [https://bugs.launchpad.net/](https://bugs.launchpad.net/) adding the file /var/log/kern.log as an attachment?

---

