---
title: "snes9x .."
date: 2005-06-02
forum: Gaming &amp; Leisure
---

### Post by somuchfortheafter on 2005-06-02
anyway under synaptic i installed snes9xexpress and gsnes9x however when i open a game to play it i recieve the following errors
```

/usr/bin/gsnes9x "/home/chris/Shared/SNES ROM Super Mario World 2 - Yoshi's Island.zip"
execvp("/usr/bin/gsnes9x", ...):
No such file or directory

- could not execute /usr/bin/gsnes9x
- make sure you have the correct snes9x path
  set in Preferences / Paths.

```

umm just to be sure the file was there i browsed to /usr/bin/ and sure enough the file was indeed there so i went under preferences and set it to execute at /usr/bin/GSnes9x just as the file was named however still i recieve the errors, any ideas?

---

### Post by somuchfortheafter on 2005-06-02
ignore what was mentioned above, i switched to znes and now the only thing not working is sound.. so if you have any suggestions there please let me know...

---

### Post by somuchfortheafter on 2005-06-02
issue is fixed solution is on the forum it involved some weird alsa package and a reboot...

---

### Post by ltmon on 2005-06-03
You could also try snes9express instead of gsnes9x.  It's working well for me.

---

