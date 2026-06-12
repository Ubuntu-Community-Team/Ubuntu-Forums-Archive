---
title: "vlc keybindings..."
date: 2006-04-13
forum: Desktop Environments
---

### Post by Jawbreaker4Fs on 2006-04-13
I have a laptop with those little play, pause keys on it.. and I was wondering how to configure these to be used with VLC. I have them set up for global key bindings in amaroK, and it lists the key as XF86AudioPlay, but I can't figure out how to use this same button in VLC. In the configuration menu for hotkeys, it allows me to press a key for use with Play/Pause, but pressing the play button doesn't seem to register with the configurator. I tried editing .vlc/vlcrc manually to change:

```

# Play/Pause (key)
#key-play-pause=Space

```

to

```

# Play/Pause (key)
#key-play-pause=XF86AudioPlay

```

but the changes were undone as soon as I launched VLC. Any suggestions?

---

