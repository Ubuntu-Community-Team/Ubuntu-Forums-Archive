---
title: "Second Xorg Session"
date: 2008-10-08
forum: Desktop Environments
---

### Post by nicol_bolas on 2008-10-08
Okay what I want to do is be able to do is to start two different x sessions at one time and to be able to switch between the two with alt-ctrl-F7 and alt-ctrl-F8.

Things that may or may not be a problem:

First is the nvidia drivers I am running. I am not using a graphic login manager and I would like to keep it that way. I am using gnome.

---

### Post by jpkotta on 2008-10-08
I assume you are using startx.

```
startx -- :0 >& /dev/null &
startx -- :1 >& /dev/null &
```

In my experience, nVidia drivers handle multiple X servers well.

---

### Post by nicol_bolas on 2008-10-08
This works. Thank-you so much

---

