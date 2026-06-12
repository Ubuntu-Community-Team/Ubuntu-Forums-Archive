---
title: "XMMS problems.."
date: 2005-10-17
forum: Desktop Environments
---

### Post by SeanCallan on 2005-10-17
Hey guys, couple XMMS questions.

First ) I can't get it to play .m4a extensions, any ideas?  Am I just missing a package?

Second ) Randomly it would seem, XMMS throws and Error and tells me to make sure my sound card is connected, etc; then it if I wait a minute or try a different song it works.

Any ideas?

---

### Post by RAOF on 2005-10-17
1) You probably need to install the xmms-mp4 package.  Xmms probably doesn't start with support for m4a (or equivalently, mp4, aac)

In general, a good first step with this sort of problem would be to go into synaptic and search (names & descriptions) for something that seems appropriate (like "xmms").  You'll get a lot of packages, and in this case, one which is appropriate :)

2) Not so sure here, but it's possible that some other program is playing sounds at the same time?  Some older programs (using OSS) don't share the sound card well.

---

### Post by iH8forcedRegistration on 2005-11-05
apt-get install soundconverter

EDIT:
Sorry. Wrong thread.

---

