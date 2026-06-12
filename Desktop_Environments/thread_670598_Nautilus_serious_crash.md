---
title: "Nautilus serious crash"
date: 2008-01-17
forum: Desktop Environments
---

### Post by ukch on 2008-01-17
Recently (ie. probably since upgrading to Gutsy), Nautilus has been crashing whenever I open a directory containing certain types of audio file (so far I have discovered the problem with ogg, flac and wav, but it probably occurs with everything). What happens is the problem directory opens up, shows the files (they have an icon of a musical note), then freezes up. The only way to return to normal service is to 'killall nautilus' or click 'force quit', whereupon nautilus is respawned. I reckon the crash is something to do with previews, but I don't know enough to test the problem out. Anyone have any ideas?

---

### Post by kellemes on 2008-01-17
Startup nautilus from the terminal and you'll probably get some more informative output.

---

### Post by ukch on 2008-01-21
OK. Any idea how I can kill Nautilus without it automatically respawning? Otherwise when I try and start it from the terminal it just opens a new window in the currently-running process.

---

### Post by ukch on 2008-02-05
I managed to start Nautilus from the terminal and I'm afraid the only outpus I got was:

```
Initializing gnome-mount extension
Killed
```

Which isn't exactly helpful. I also tried searching for a verbose setting but couldn't find one. Can anyone help?

---

