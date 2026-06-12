---
title: "Installing Dxx-rebirth Fails With &quot;undefined reference to `jukebox_exts'&quot;"
date: 2011-01-24
forum: Gaming &amp; Leisure
---

### Post by user2037 on 2011-01-24
Any idea why installing Dxx-rebirth (1 and 2) fail with the following:
> 
Linking d2x-rebirth-gl ...
main/menu.o: In function `sound_menuset':
menu.c:(.text+0xd9d): undefined reference to `jukebox_exts'
menu.c:(.text+0xec9): undefined reference to `jukebox_exts'
menu.c:(.text+0x1001): undefined reference to `jukebox_exts'
menu.c:(.text+0x1041): undefined reference to `jukebox_exts'
menu.c:(.text+0x1091): undefined reference to `jukebox_exts'
collect2: ld returned 1 exit status
scons: *** [d2x-rebirth-gl] Error 1
scons: building terminated because of errors.


Apparently one needs only to add "sdlmixer=1" to the Scons command.

---

