---
title: "Mumble Overlay in TF2 Linux?"
date: 2013-06-21
forum: Gaming &amp; Leisure
---

### Post by xbanane on 2013-06-21
Ive tried many times to get mumble-overlay working with TF2.

Stuff like: "mumble-overlay steam" then launching TF, "mumble-oberlay steam steam://rungameid/440", "mumble-overlay <steampath>/SteamApps/common/Team\ Fortress\ 2/hl2_linux -game TF"

But I got an error message at *LD_PRELOAD=/usr/lib/mumble/libmumble.so mumble-overlay steam steam://rungameid/440*:
```
jp@jp-ubuntu:~% LD_PRELOAD=/usr/lib/mumble/libmumble.so mumble-overlay steam steam://rungameid/440
set
ERROR: ld.so: object '/usr/lib32/mumble/libmumble.so.1' from LD_PRELOAD cannot be preloaded: ignored.
ERROR: ld.so: object '/usr/lib32/mumble/libmumble.so.1' from LD_PRELOAD cannot be preloaded: ignored.
ERROR: ld.so: object '/usr/lib32/mumble/libmumble.so.1' from LD_PRELOAD cannot be preloaded: ignored.
ERROR: ld.so: object '/usr/lib32/mumble/libmumble.so.1' from LD_PRELOAD cannot be preloaded: ignored.
ERROR: ld.so: object '/usr/lib32/mumble/libmumble.so.1' from LD_PRELOAD cannot be preloaded: ignored.
ERROR: ld.so: object '/usr/lib32/mumble/libmumble.so.1' from LD_PRELOAD cannot be preloaded: ignored.
ERROR: ld.so: object '/usr/lib32/mumble/libmumble.so.1' from LD_PRELOAD cannot be preloaded: ignored.
ERROR: ld.so: object '/usr/lib32/mumble/libmumble.so.1' from LD_PRELOAD cannot be preloaded: ignored.
ERROR: ld.so: object '/usr/lib32/mumble/libmumble.so.1' from LD_PRELOAD cannot be preloaded: ignored.
ERROR: ld.so: object '/usr/lib32/mumble/libmumble.so.1' from LD_PRELOAD cannot be preloaded: ignored.
ERROR: ld.so: object '/usr/lib32/mumble/libmumble.so.1' from LD_PRELOAD cannot be preloaded: ignored.
ERROR: ld.so: object '/usr/lib32/mumble/libmumble.so.1' from LD_PRELOAD cannot be preloaded: ignored.
ERROR: ld.so: object '/usr/lib32/mumble/libmumble.so.1' from LD_PRELOAD cannot be preloaded: ignored.
ERROR: ld.so: object '/usr/lib32/mumble/libmumble.so.1' from LD_PRELOAD cannot be preloaded: ignored.
ERROR: ld.so: object '/usr/lib32/mumble/libmumble.so.1' from LD_PRELOAD cannot be preloaded: ignored.
ERROR: ld.so: object '/usr/lib32/mumble/libmumble.so.1' from LD_PRELOAD cannot be preloaded: ignored.
ERROR: ld.so: object '/usr/lib32/mumble/libmumble.so.1' from LD_PRELOAD cannot be preloaded: ignored.
ERROR: ld.so: object '/usr/lib32/mumble/libmumble.so.1' from LD_PRELOAD cannot be preloaded: ignored.
ERROR: ld.so: object '/usr/lib32/mumble/libmumble.so.1' from LD_PRELOAD cannot be preloaded: ignored.
Running Steam on ubuntu 12.04 64-bit
ERROR: ld.so: object '/usr/lib32/mumble/libmumble.so.1' from LD_PRELOAD cannot be preloaded: ignored.
STEAM_RUNTIME is enabled automatically
ERROR: ld.so: object '/usr/lib32/mumble/libmumble.so.1' from LD_PRELOAD cannot be preloaded: ignored.
ERROR: ld.so: object '/usr/lib32/mumble/libmumble.so.1' from LD_PRELOAD cannot be preloaded: ignored.
ERROR: ld.so: object '/usr/lib32/mumble/libmumble.so.1' from LD_PRELOAD cannot be preloaded: ignored.
ERROR: ld.so: object '/usr/lib32/mumble/libmumble.so.1' from LD_PRELOAD cannot be preloaded: ignored.
ERROR: ld.so: object '/usr/lib32/mumble/libmumble.so.1' from LD_PRELOAD cannot be preloaded: ignored.
ERROR: ld.so: object '/usr/lib32/mumble/libmumble.so.1' from LD_PRELOAD cannot be preloaded: ignored.
ERROR: ld.so: object '/usr/lib32/mumble/libmumble.so.1' from LD_PRELOAD cannot be preloaded: ignored.
ERROR: ld.so: object '/usr/lib32/mumble/libmumble.so.1' from LD_PRELOAD cannot be preloaded: ignored.
ERROR: ld.so: object '/usr/lib/mumble/libmumble.so.1' from LD_PRELOAD cannot be preloaded: ignored.
ERROR: ld.so: object '/usr/lib/mumble/libmumble.so' from LD_PRELOAD cannot be preloaded: ignored.
ERROR: ld.so: object '/usr/lib/mumble/libmumble.so.1' from LD_PRELOAD cannot be preloaded: ignored.
ERROR: ld.so: object '/usr/lib/mumble/libmumble.so' from LD_PRELOAD cannot be preloaded: ignored.
jp@jp-ubuntu:~% 
```

---

### Post by xbanane on 2013-07-06
I think I know why it isn't working:

[http://mumble.sourceforge.net/Overlay](http://mumble.sourceforge.net/Overlay), 2nd table.

[TABLE="class: sortable"]
[TR]
[TD]OpenGL 
[/TD]
[TD] x64 [/TD]
[TD] Any [/TD]
[TD] [COLOR=#883333]does not display[/COLOR]
[/TD]
[/TR]
[/TABLE]

So that TF2 is using 64 bit but other games not.

---

