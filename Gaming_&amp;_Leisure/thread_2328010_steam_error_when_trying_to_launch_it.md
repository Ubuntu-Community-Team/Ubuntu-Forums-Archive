---
title: "steam error when trying to launch it"
date: 2016-06-16
forum: Gaming &amp; Leisure
---

### Post by juha-karmala on 2016-06-16
I just installed Steam and I get error message when I try to launch it. 

```
:~$ steam
Running Steam on ubuntu 16.04 64-bit
STEAM_RUNTIME is enabled automatically
Installing breakpad exception handler for appid(steam)/version(0)
libGL error: unable to load driver: r600_dri.so
libGL error: driver pointer missing
libGL error: failed to load driver: r600
libGL error: unable to load driver: swrast_dri.so
libGL error: failed to load driver: swrast
```

---

### Post by QDR06VV9 on 2016-06-16
With the help from a user comment, [http://www.reddit.com/r/linux_gaming/co](http://www.reddit.com/r/linux_gaming/co) … rom_steam/ I located the files
libstdc++

and
libgcc_s

and removed them. After that I was able to load up steam. Now because I tried a crapload of things I don't know if doing this will really solve the problem, it did for me, so hopefully it will for others. Please report back!
Remove libstdc++

```
rm ~/.local/share/Steam/ubuntu12_32/steam-runtime/amd64/installed/libstdc++6-4.6-pic_4.6.3-1ubuntu5+srt4_amd64 && rm ~/.local/share/Steam/ubuntu12_32/steam-runtime/amd64/installed/libstdc++6-4.6-pic_4.6.3-1ubuntu5+srt4_amd64.md5 && rm ~/.local/share/Steam/ubuntu12_32/steam-runtime/amd64/installed/libstdc++6_4.8.1-2ubuntu1~12.04+steamrt2+srt1_amd64 && rm ~/.local/share/Steam/ubuntu12_32/steam-runtime/amd64/installed/libstdc++6_4.8.1-2ubuntu1~12.04+steamrt2+srt1_amd64.md5 && rm ~/.local/share/Steam/ubuntu12_32/steam-runtime/amd64/usr/lib/gcc/x86_64-linux-gnu/4.6/libstdc++_pic.a && rm ~/.local/share/Steam/ubuntu12_32/steam-runtime/amd64/usr/lib/gcc/x86_64-linux-gnu/4.6/libstdc++_pic.map && rm ~/.local/share/Steam/ubuntu12_32/steam-runtime/amd64/usr/lib/x86_64-linux-gnu/libstdc++.so.6 && rm ~/.local/share/Steam/ubuntu12_32/steam-runtime/amd64/usr/lib/x86_64-linux-gnu/libstdc++.so.6.0.18 && rm ~/.local/share/Steam/ubuntu12_32/steam-runtime/amd64/usr/share/doc/libstdc++6 && rm ~/.local/share/Steam/ubuntu12_32/steam-runtime/amd64/usr/share/doc/libstdc++6-4.6-pic && rm ~/.local/share/Steam/ubuntu12_32/steam-runtime/i386/installed/libstdc++6-4.6-pic_4.6.3-1ubuntu5+srt4_i386 && rm ~/.local/share/Steam/ubuntu12_32/steam-runtime/i386/installed/libstdc++6-4.6-pic_4.6.3-1ubuntu5+srt4_i386.md5 && rm ~/.local/share/Steam/ubuntu12_32/steam-runtime/i386/installed/libstdc++6_4.8.1-2ubuntu1~12.04+steamrt2+srt1_i386 && rm ~/.local/share/Steam/ubuntu12_32/steam-runtime/i386/installed/libstdc++6_4.8.1-2ubuntu1~12.04+steamrt2+srt1_i386.md5 && rm ~/.local/share/Steam/ubuntu12_32/steam-runtime/i386/usr/lib/gcc/i686-linux-gnu/4.6/libstdc++_pic.a && rm ~/.local/share/Steam/ubuntu12_32/steam-runtime/i386/usr/lib/gcc/i686-linux-gnu/4.6/libstdc++_pic.map && rm ~/.local/share/Steam/ubuntu12_32/steam-runtime/i386/usr/lib/i386-linux-gnu/libstdc++.so.6 && rm ~/.local/share/Steam/ubuntu12_32/steam-runtime/i386/usr/lib/i386-linux-gnu/libstdc++.so.6.0.18 && rm ~/.local/share/Steam/ubuntu12_32/steam-runtime/i386/usr/share/doc/libstdc++6 && rm ~/.local/share/Steam/ubuntu12_32/steam-runtime/i386/usr/share/doc/libstdc++6-4.6-pic && rm ~/.local/share/Steam/ubuntu12_32/steam-runtime.old/i386/usr/share/doc/libstdc++6

```

Remove libgcc_s

```
rm ~/.local/share/Steam/ubuntu12_32/steam-runtime/amd64/lib/x86_64-linux-gnu/libgcc_s.so.1 && rm ~/.local/share/Steam/ubuntu12_32/steam-runtime/i386/lib/i386-linux-gnu/libgcc_s.so.1

```
There may be more of these files you have to remove, so try these commands first, then run updatedb command  and try and locate any of these librarires again. (If you get command not found when running updatedb you need to install the [B]mlocate package)
[/B]
I also ran
```
rm ~/.local/share/Steam/ubuntu12_32/steam-runtime/i386/usr/lib/i386-linux-gnu/libxcb.so.1

```
at some point but I dobut that does anything. Steam replaces these files very frequently so I would make sure to save this in a document, or a .sh file so you can just execute them whenever they come back.
Hope this works for you as well.

---

### Post by juha-karmala on 2016-06-16
[http://steamcommunity.com/app/221410/discussions/0/412446292752412961/#c412446292752457261](http://steamcommunity.com/app/221410/discussions/0/412446292752412961/#c412446292752457261) this solved my issue!

---

### Post by QDR06VV9 on 2016-06-16
That is great now if you would please mark your thread as solved as to help others with similar issue's 
To mark as solved see my Signature.
Regards

---

