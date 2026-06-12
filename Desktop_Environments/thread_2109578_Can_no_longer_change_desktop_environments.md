---
title: "Can no longer change desktop environments"
date: 2013-01-28
forum: Desktop Environments
---

### Post by cg40k on 2013-01-28
So installed Cinnamon today and went to try it out only to find I can no longer log into any other desktop environment other than Ubuntu(default). Any help?

---

### Post by hydn79 on 2013-01-28
You mean you can no longer access unity?

What version of Ubuntu are you using? I know on 11.10 I did:
sudo apt-get install gnome-session-fallback

...which allowed switching.

---

### Post by cg40k on 2013-01-28
Actually I fixed the problem. Apparently I had too many desktop environments and the de selection list would not let me click okay *LULZ*

---

### Post by hydn79 on 2013-01-28
So what did you think of Cinnamon? Keeper?

---

### Post by cg40k on 2013-01-28
I don't know. I like it, don't get me wrong, but it feels a lot like KDE (which I have installed and have been using a lot)

The themes for Cinnamon help though. All this is just cosmetic though. As far as functionality goes its great, and I think I enjoy it in that aspect more so than Unity or Gnome3.

Something of note I thought about though; is there a known issue with the selection menu for desktop environments and having over a certain number that causes you to be unable to log into a non-default d.e.?

---

### Post by VanillaMozilla on 2013-01-29
> **cg40k said:**
> Something of note I thought about though; is there a known issue with the selection menu for desktop environments and having over a certain number that causes you to be unable to log into a non-default d.e.?
Oh my gosh, yes.  See [bug 1052453,](https://bugs.launchpad.net/ubuntu/+source/unity-greeter/+bug/1052453) for example.  Take a look [here](http://ubuntuforums.org/showthread.php?p=12468753#post12468753) for a workaround.

---

