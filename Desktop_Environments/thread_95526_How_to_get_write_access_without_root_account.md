---
title: "How to get write access without root account?"
date: 2005-11-26
forum: Desktop Environments
---

### Post by Barnaby on 2005-11-26
Hi all, just joined up and this is my second post here. Have been using Ubuntu for a while now, on and and off. The one thing that flabbergasted me is how do you get things done without a root account? I mean it's impossible to change anything outside your home folder as you're not allowed to change file and folder permissions.
I've been using Debian and Vector before and got more accustomed to the traditional way of doing things I guess. But there must be a way.
Would like to change the brown splash screen for example into something else, and there are some more in the usr/share/pixmaps/splash directory, but how to change? And how to get my own in there as it doesn't let me write.

Is it possible to change the unlock prompt (when you come out of screensaver) from Ubuntu to something else like more traditional Debian style?

Apart from this I'm very happy with Ubuntu, am using it for the way more up to date Gnome desktop and software, just don't particularly care for the brown ;) .

Thanks, that's quite a bit for the beginning.

Barnaby

---

### Post by Xian on 2005-11-26
From the wiki: [How-To Sudo Command](https://wiki.ubuntu.com/RootSudo?action=show&redirect=RootPrivileges).

---

### Post by Barnaby on 2005-11-26
Thanks, that was useful. However one question still remains - can I change the unlock screenie and if where is it located to replace it?

Ta, Barnaby

---

### Post by aysiu on 2005-11-26
Do you like to do things graphically? If so, create a launcher with the command ```
gksudo nautilus
``` When you want to make root changes to a file, click on that launcher.

---

