---
title: "ARK: Failed to start game (missing executable)."
date: 2017-02-11
forum: Gaming &amp; Leisure
---

### Post by fluffymcmuffins on 2017-02-11
Hello, I recently installed Steam and didn't have any issues with that, but when I installed and tried to run ARK I get "Failed to start game (missing executable)." 

I have searched around for other people having this issue, but I haven't run into any that fit my scenario or that have helpful solutions. 

I'm very new to using Ubuntu and I'm not sure what information would help resolve this issue, so if there's anything I can provide let me know. ^_^

The only thing I have tried so far is verifying the file integrity.

---

### Post by Perfect Storm on 2017-02-11
Sounds like a problem with the game within Steam - you should properly go the developers of the game. If there is missing a file(s) there's nothing we can do.

EDIT: You could check .steam/steam/steamapps/common/ARK and see if there's binaries you can run.

---

### Post by oldrocker99 on 2017-02-11
You might also try uninstalling the game, and then reinstalling it. As a long-time Steam for Linux user, some games have had the "missing executable" error, which eventually was fixed. I don't know about ARK.

---

### Post by fluffymcmuffins on 2017-02-11
Yeah tried uninstalling/reinstalling a moment ago, same error. =/ 

What do you mean by see if there's any binaries I can run? Sorry very new to this sort of thing.

---

### Post by oldrocker99 on 2017-02-11
Look at Properties. and Local Files. You want to look for (in icon mode) a diamond-shaped icon, which indicates an executable file. If you don't see one, you indeed have a missing executable.

---

### Post by fluffymcmuffins on 2017-02-12
When I go into Local files there are three folders in C:\Program Files\Steam\steamapps\common\ARK\_CommonRedist\vcredist labeled 2010, 2012, and 2013. Each of those three folders have two executables in them named vcredist_x64.exe and vcredist_x86.exe. So it appears the executables are there, but I guess it's not recognizing them for some reason. Or it's looking in the wrong place. Is there a way to run the executables manually rather than through the steam library?

---

### Post by oldrocker99 on 2017-02-12
You can cd to that directory, and then type```
./nameofprogram
```

Please post the results.

---

### Post by kloszard on 2017-02-12
> **fluffymcmuffins said:**
> When I go into Local files there are three folders in C:\Program Files\Steam\steamapps\common\ARK\_CommonRedist\vcredist labeled 2010, 2012, and 2013...

Hi, Why does your path looks so windows-like? I would expect something like:

```

/home/<user_name>/.steam/steam/steamapps/common/<game_name>/_CommonRedist/vcredist
```

---

### Post by jim_deadlock on 2017-12-21
For the benefit of anyone experiencing the "missing executable" error in future, this is a very common problem that affects many Steam games, especially ones with "new" Linux versions that were Win-only previously. It's caused by the game developer not managing to properly upload the Linux version to the Steam repository. I've been told that the Linux setup is buried deep in the Steamworks system that devs use to set up their games and store pages on Steam, and many of them can't work out how to do it despite having a perfectly good working Linux version available. Very frustrating for everyone concerned. There are several Linux-pending games I've been pestering the devs about for months :(

---

