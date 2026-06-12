---
title: "No Visual Effects with ATI X1250 integrated"
date: 2007-10-19
forum: Desktop Effects &amp; Customization
---

### Post by CosminGC on 2007-10-19
So I have an integrated ATI X1250 with glx working, a fresh Ubuntu 7.10 and when I enable Visual Effects I get the message: The Composite extension is not available

Is there any way to enable the Visual Effects?

---

### Post by CosminGC on 2007-10-19
I found the answer [here]("http://ubuntuforums.org/showpost.php?p=3572847&postcount=19"):

```
sudo apt-get install xserver-xgl compiz compizconfig-settings-manager
```
for ATI  and restart X,

---

