---
title: "Harvest: Massive Encounter unresolved dependencies"
date: 2013-02-26
forum: Gaming &amp; Leisure
---

### Post by myromance123 on 2013-02-26
Hi there,

Alright I've been trying frantically to get this game working on my Ubuntu 12.10 64Bit system. Right there is the problem, 64Bit.

Anyhow, down to the specific matter at hand. When I run the game in Harvest's folder through a Terminal like so:
```
./Harvest
```

I get this error:
```
./Harvest: error while loading shared libraries: libsfml-system.so.2: cannot open shared object file: No such file or directory
```

I checked the Synaptic Package Manager, and I can only find SFML 1.6. I do not wish to compile SFML 2.0 myself, so how can I go about this? Is there a way to get this silly dependency resolved? Or do I have to wait for a future Ubuntu version that may or may not have this?

The developer developed the game with ONLY 32Bit in mind. The script that starts out at when you begin the game only searches for the libraries, without checking if they're 32bit or 64bit.

After running:
```
sudo apt-get install ia32-libs
```

I had pretty much resolved all the dependencies except the Nvidia-cg-toolkit one. I just ran:
```
sudo apt-get install nvidia-cg-toolkit:i386
```

That removes my 64bit version of the library, but I haven't had any issues with my other games yet. If I manage to resolve this SFML dependency, there's no guarantee I'll be able to play the game. Trying is still better than nothing though.

Any help or guidance is greatly appreciated!

---

### Post by myromance123 on 2013-02-27
Bump. Is there any way to resolve this libsfml dependency in Ubuntu 12.10?

How are Ubuntu gamer's playing this game? I'd really like to be able to play it, and make a game recording video of it :D

Any help is appreciated, I've googled quite a bit but haven't seen anyone else with this issue. Does Ubuntu 12.04 ship with sfml 2.0? It would be strange if it did and 12.10 didn't...

---

