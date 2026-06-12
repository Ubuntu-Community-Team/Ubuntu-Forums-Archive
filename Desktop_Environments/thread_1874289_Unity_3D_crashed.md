---
title: "Unity 3D crashed"
date: 2011-11-02
forum: Desktop Environments
---

### Post by singampk on 2011-11-02
Hi Guys,

I recently upgrade to 11.10 from 11.04, when I am exploring some features in unity. Suddenly the top menu is vanished and Side Bar(Unity 3D bar) in not opening anymore. Impact of this is I could able to open only the items on the desktop. Even the I am not able to open the terminal also.

PS: I am able to ssh to the box and get the terminal access, when I run the metacity --replace, its saying unable to replace.

Thanks,
Krishna

---

### Post by enkay009 on 2011-11-02
Try **unity --replace**.

Also you don't have to SSH to the machine if it's local. You can alternatively use a terminal on the machine with CTRL+ALT+F1. 

You might need to set the display first in your shell.

```
export DISPLAY=:0
```

---

### Post by Mark Phelps on 2011-11-02
You could try the solution in the linked thread:

[http://ubuntuforums.org/showthread.php?t=1874076]("http://ubuntuforums.org/showthread.php?t=1874076")

---

