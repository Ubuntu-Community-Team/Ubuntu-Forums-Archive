---
title: "LinuxDC++ compiling help"
date: 2009-03-07
forum: General Help
---

### Post by inspirations365 on 2009-03-07
So I have the source code for 1.0.2 and I needed to patch the files. This is all good and done, but now how do I build the application? I've looked at the guide posted here, but I don't think that's what I'm looking for. Can anyone help me?

---

### Post by Xiong Chiamiov on 2009-03-07
[https://help.ubuntu.com/community/CompilingEasyHowTo](https://help.ubuntu.com/community/CompilingEasyHowTo)

---

### Post by inspirations365 on 2009-03-07
Okay, thanks for the link. I've inppput the command

```
patch -p0 linuxdcpp-1.0.2-ruxan.patch
``` and now my terminal is just sitting there, not giving me another prompt. The patch wasn't very big at all...Am i just supposed to wait until it's done?

---

### Post by inspirations365 on 2009-03-07
Never mind, got it. The correct command is ```
patch -p0 < patch-file-name-here
```

Don't forget the "<" symbol!

---

