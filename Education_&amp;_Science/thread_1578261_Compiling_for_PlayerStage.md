---
title: "Compiling for Player/Stage"
date: 2010-09-20
forum: Education &amp; Science
---

### Post by erupter on 2010-09-20
Hullo.
Succeded in installing player&stage, they work.
I then went for installing and compiling the examples.
Once it worked, then it failed.
Since one example (service_discovery.c) did not compile, i erased everything, modified the CMakeLists.txt and added the source.
It failed to compile.
Ok reverted back to default by unpacking the tar ex novo and then it won't compile nothing.
When hitting *make* it can't find the includes.
Looks like there isn't some path or whatever.
I don't know.
My CPATH has 
/usr/local/include
/usr/include

the shell output is this
```
erupter@erupter-desktop:~/Scrivania/player-3.0.1/examples/build$ make
[ 33%] Building C object CMakeFiles/simple.dir/simple.o
/home/erupter/Scrivania/player-3.0.1/examples/libplayerc/simple.c:31:32: error: libplayerc/playerc.h: No such file or directory
/home/erupter/Scrivania/player-3.0.1/examples/libplayerc/simple.c: In function ‘main’:
/home/erupter/Scrivania/player-3.0.1/examples/libplayerc/simple.c:37: error: ‘playerc_client_t’ undeclared (first use in this function)
/home/erupter/Scrivania/player-3.0.1/examples/libplayerc/simple.c:37: error: (Each undeclared identifier is reported only once
/home/erupter/Scrivania/player-3.0.1/examples/libplayerc/simple.c:37: error: for each function it appears in.)
/home/erupter/Scrivania/player-3.0.1/examples/libplayerc/simple.c:37: error: ‘client’ undeclared (first use in this function)
/home/erupter/Scrivania/player-3.0.1/examples/libplayerc/simple.c:38: error: ‘playerc_position2d_t’ undeclared (first use in this function)
/home/erupter/Scrivania/player-3.0.1/examples/libplayerc/simple.c:38: error: ‘position2d’ undeclared (first use in this function)
/home/erupter/Scrivania/player-3.0.1/examples/libplayerc/simple.c:47: error: ‘PLAYER_OPEN_MODE’ undeclared (first use in this function)
make[2]: *** [CMakeFiles/simple.dir/simple.o] Error 1
make[1]: *** [CMakeFiles/simple.dir/all] Error 2
make: *** [all] Error 2
```

The first missing path is in /usr/local/include/player-3.0/libplayerc
I don't think i should manually add every single directory.
What can i do?

---

