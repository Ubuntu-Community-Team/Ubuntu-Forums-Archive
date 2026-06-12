---
title: "changing the default text editor"
date: 2006-04-17
forum: Desktop Environments
---

### Post by Goonie on 2006-04-17
Hey all

I'm wondering how I change my default text editor (in terminal) from vim to nano ? 

Goonie

---

### Post by juicybananahead on 2006-04-17
Long answer: [http://ubuntuforums.org/showthread.php?t=155826&highlight=export+editor](http://ubuntuforums.org/showthread.php?t=155826&highlight=export+editor)

Short answer: ```
EDITOR=nano; export EDITOR
```

// Dave

---

### Post by ape on 2006-04-18
`sudo update-alternatives --config editor`

This will bring up a list of the available text editors (for the console) and allow you to choose the one that you want to use as the default.

---

