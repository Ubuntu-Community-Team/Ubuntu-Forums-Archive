---
title: "Heroes 3 change resolution, it's out of range"
date: 2012-03-27
forum: Gaming &amp; Leisure
---

### Post by Subidubi32 on 2012-03-27
I have isntalled heroes3 native to my Ubuntu(x86),an I have patched it too.
> heroes3 -v
Heroes of Might & Magic III 1.3.1a
Built with glibc-2.1 on x86
Then it couldn't open the audio, because of the OSS:
> Couldn't open audio:
I downloaded some extra files:
[http://www.swanson.ukfsn.org/loki/](http://www.swanson.ukfsn.org/loki/)
Extracted to:
> /usr/local/lib
> sudo LD_PRELOAD=/usr/local/lib/Loki_Compat/libstdc++-3-libc6.2-2-2.10.0.so:/usr/local/lib/Loki_Compat/libsmpeg-0.4.so.0.1.3:/usr/local/lib/Loki_Compat/libsmjpeg-0.2.so.0:/usr/local/lib/Loki_Compat/libSDL_mixer-1.2.so.0 /usr/local/games/Heroes3/heroes3.dynamic -w
And finally the audio is working, but now there is problem with the video. With this -w its running fine in windowed mode, but if you don't launch it in windowed, I think the resolution, or refresh rate 'out of range'-says my monitor. How could I change its resolution or refresh rate?

---

### Post by Perfect Storm on 2012-03-27
Try see if there's a help command to the game -h or --help to see if you can set the resolution via switches.

Also check if the game have a config file/folder in your home directory (usually hidden).

---

