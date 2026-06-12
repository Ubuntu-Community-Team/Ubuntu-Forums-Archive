---
title: "skippy graphics for some reason"
date: 2006-09-19
forum: Desktop Environments
---

### Post by oldmanstan on 2006-09-19
my system has been working just fine for quite some time now. i recently installed xfce (through the xubuntu-desktop package) and now suddenly when i run games the video is smooth but then every couple seconds it hangs for maybe .25 or .5 seconds. i switched back to gnome and it still does it (i didn't uninstall xfce, just changed the one i was using).

any ideas about what could be the cause? xfce might not be the culprit so if anyone has any general ideas that'd be great too.

thanks

---

### Post by jISh on 2006-09-19
Do you have your video drivers installed properly? Direct rendering works?
```

lsmod |grep direct

```

---

### Post by oldmanstan on 2006-09-19
i dont get anything returned on that, although like i said, the video used to work fine. i have the nvidia drivers install (nvidia-glx in the repositories)

---

