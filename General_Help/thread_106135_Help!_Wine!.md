---
title: "Help! Wine!"
date: 2005-12-19
forum: General Help
---

### Post by Prudentissimus on 2005-12-19
> prudens@lin:~/Desktop/wine-20040615$ ./tools/wineinstall
WINE Installer v0.74

Running configure...

configure: creating cache config.cache
checking build system type... i686-pc-linux-gnulibc1
checking host system type... i686-pc-linux-gnulibc1
checking whether make sets $(MAKE)... no
checking for gcc... gcc
checking for C compiler default output file name... configure: error: C compiler cannot create executables
See `config.log' for more details.

Configure failed, aborting install.
prudens@lin:~/Desktop/wine-20040615$




What should I do?

---

### Post by invalid on 2005-12-19
```
sudo apt-get install build-essential
```

---

### Post by 23meg on 2005-12-19
Try ```
sudo apt-get install build-essential
```

---

### Post by Prudentissimus on 2005-12-19
but this version of wine is not an "essential,"


it is an older version.... which I need to run a game... (sadly that game seems to work not with the latest WINE version.)

---

### Post by Ocxic on 2005-12-20
just intall biuld-essential, it's just a package thats includes what you neet to compile program, and let gcc compile executibles

---

### Post by invalid on 2005-12-20
build-essential has nothing to do with wine. It is simply a package that includes the essentials to building and compiling software.

---

