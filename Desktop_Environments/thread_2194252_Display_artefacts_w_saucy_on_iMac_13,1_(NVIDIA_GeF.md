---
title: "Display artefacts w/ saucy on iMac 13,1 (NVIDIA GeForce GT 650M)"
date: 2013-12-17
forum: Desktop Environments
---

### Post by albrecht.dress on 2013-12-17
Hi all,

I run Ubuntu 'saucy' on an iMac 13,1 (i5, 2.9 GHz) which comes with a NVIDIA GeForce GT 650M.  Both Mac OS X and Linux are installed, and the box is booted using rEFInd ([http://www.rodsbooks.com/refind/](http://www.rodsbooks.com/refind/)).

Using the Nouveau driver, I see *really* annoying display artefacts: at the right border of the display, sometimes bright horizontal "sparks" briefly appear, approximately 10..20% of the total screen width.

Unfortunately, it is not possible to use the Nvidia driver, due to the ' EVO Push buffer channel allocation failed' bug (neither the one coming with saucy, nor the one from Nvidia; see [https://devtalk.nvidia.com/default/topic/573252/linux/evo-push-buffer-channel-allocation-failed-is-back-as-usedplib-false-no-more-supported-with-325-15/2/](https://devtalk.nvidia.com/default/topic/573252/linux/evo-push-buffer-channel-allocation-failed-is-back-as-usedplib-false-no-more-supported-with-325-15/2/)).  Thus, I could not check if the artefacts are related to the Nouveau driver or to something else.  I can only say that they do not occur with Mac OS X...

Any help for solving this issue would be highly appreciated!

Thanks in advance,
Albrecht.

---

