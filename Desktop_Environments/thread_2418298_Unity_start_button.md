---
title: "Unity start button"
date: 2019-05-04
forum: Desktop Environments
---

### Post by cwm.030 on 2019-05-04
I have a problem with Unity. 

I noticed that if I click " the start menu" aka the Ubuntu menu button sometimes it wont activate the menu until I change workspaces and then go back to the work space I was on and click the start button again. And then it works fine...

 Any ideas why this could be happening and how do I fix it?

Ubuntu 18.04 --- Upgraded from 16.04

Thanks,
Chris

---

### Post by DuckHook on 2019-05-04
Possibly because you are running Unity in an environment for which it was not truly designed. Canonical switched to Gnome3 as of Artful. Unity is maintained for Xenial, but not for Bionic. It can still be used, but this must be considered a kludge&#8212;a legacy of the past&#8212;like the appendix we all carry around in our personal plumbing.

Not sure how to even advise you here. I still have Unity, but it's on a Xenial partition. My Bionic partition runs Gnome3 problem-free.

Any reason you are still on Unity?

---

### Post by mc4man on 2019-05-05
Haven't seen anything like that in a couple of 18.04 installs using a unity session. They work fine here.

Your issue probably  is from a 16.04 to 18.04 upgrade as there were significant changes. If inclined to continue to use a unity session then best bet is a fresh 18.04.x install, then install unity session.
(- done by installing the ubuntu-unity-desktop package, adding [this ppa ]("https://launchpad.net/~unity7maintainers/+archive/ubuntu/unity7-desktop")for a couple of fixes, best to switch to lightdm though unity session is ok with gdm3..

Otherwise try deleting ~/.compiz  ~/.config/compiz-1  folders, log out/in (likely little help..

---

### Post by cwm.030 on 2019-05-05
I just liked it.

 bummer about 18.04

---

### Post by DuckHook on 2019-05-05
> **cwm.030 said:**
> I just liked it.
Yeah. I did too. Never understood the visceral disgust that greeted it initially.
> bummer about 18.04
Same feeling here. I guess one moves on from one's losses.

Good Luck & Happy Ubuntu-ing!

---

