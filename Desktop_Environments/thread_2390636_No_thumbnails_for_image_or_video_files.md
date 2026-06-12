---
title: "No thumbnails for image or video files"
date: 2018-04-30
forum: Desktop Environments
---

### Post by alt.dot-travelling on 2018-04-30
Hi, I've just updated to 18.04 and can't get thunar to display thumbnails for image or video files.

In a file manager window, i've gone to edit --> preferences and made sure Show thumbnails was selected as Always.

Going through synaptic I have libtumbler-1-0, tumbler, tumbler-common & tumbler-plugins-extra (all version 0.2.1-0ubuntu1) installed.

Any help would be appreciated.
Thanks

---

### Post by Xian on 2018-04-30
Couple of things ....


Clear out the thumbnail cache at:
$HOME/.cache/thumbnails

Do the same at:
$HOME/.thumbnails

Any change?

---

### Post by alt.dot-travelling on 2018-05-01
That did the job.

cd into both locations and used sudo rm -rf *
rebooted and problem solved.

Thank you very, very much

---

### Post by wjurry on 2019-01-04
> **Xian said:**
> Couple of things ....


Clear out the thumbnail cache at:
$HOME/.cache/thumbnails

Do the same at:
$HOME/.thumbnails

Any change?

Thanks very much. It works for me too.

---

