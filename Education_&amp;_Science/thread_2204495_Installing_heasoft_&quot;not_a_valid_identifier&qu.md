---
title: "Installing heasoft: &quot;not a valid identifier&quot;"
date: 2014-02-08
forum: Education &amp; Science
---

### Post by carpenter-nicholas on 2014-02-08
I'm trying to install a package called heasoft in order to do some astronomy research. I can't seem to get the commands to work, even though I'm following the instructions to the t as far as I can tell. Here is the instruction page: [http://heasarc.gsfc.nasa.gov/docs/software/lheasoft/install.html](http://heasarc.gsfc.nasa.gov/docs/software/lheasoft/install.html)


Here are the various ways I've tried to type the commands. It's a standard pre-built binary, as I'm not advanced enough to mess with the source code.


nick@nick-MacBookPro:~/Downloads/heasoft-6.15.1/x86_64-unknown-linux-gnu-libc2.5/BUILD_DIR$ export HEADAS=/home/nick/Downloads/heasoft-6.15.1/x86_64-unknown-linux-gnu-libc2.5. $HEADAS/headas-init.sh
bash: export: `/home/nick/Downloads/heasoft-6.15.1/x86_64-unknown-linux-gnu-libc2.5/./headas-init.sh': not a valid identifier
[1]+  Done                    ./configure > config.out 2>&1
nick@nick-MacBookPro:~/Downloads/heasoft-6.15.1/x86_64-unknown-linux-gnu-libc2.5/BUILD_DIR$ export HEADAS=/home/nick/Downloads/heasoft-6.15.1/x86_64-unknown-linux-gnu-libc2.5/. $HEADAS/headas-init.sh
bash: export: `/home/nick/Downloads/heasoft-6.15.1/x86_64-unknown-linux-gnu-libc2.5./headas-init.sh': not a valid identifier
nick@nick-MacBookPro:~/Downloads/heasoft-6.15.1/x86_64-unknown-linux-gnu-libc2.5/BUILD_DIR$ export HEADAS=/home/nick/Downloads/heasoft-6.15.1/x86_64-unknown-linux-gnu-libc2.5/BUILD_DIR. $HEADAS/headas-init.sh
bash: export: `/home/nick/Downloads/heasoft-6.15.1/x86_64-unknown-linux-gnu-libc2.5/./headas-init.sh': not a valid identifier
nick@nick-MacBookPro:~/Downloads/heasoft-6.15.1/x86_64-unknown-linux-gnu-libc2.5/BUILD_DIR$ export HEADAS=/home/nick/Downloads/heasoft-6.15.1/x86_64-unknown-linux-gnu-libc2.5/BUILD_DIR/. $HEADAS/headas-init.sh
bash: export: `/home/nick/Downloads/heasoft-6.15.1/x86_64-unknown-linux-gnu-libc2.5/BUILD_DIR./headas-init.sh': not a valid identifier
nick@nick-MacBookPro:~/Downloads/heasoft-6.15.1/x86_64-unknown-linux-gnu-libc2.5/BUILD_DIR$ export HEADAS=/home/nick/Downloads/heasoft-6.15.1/x86_64-unknown-linux-gnu-libc2.5/BUILD_DIR/. $HEADAS/headas-init.sh
bash: export: `/home/nick/Downloads/heasoft-6.15.1/x86_64-unknown-linux-gnu-libc2.5/BUILD_DIR/./headas-init.sh': not a valid identifier
nick@nick-MacBookPro:~/Downloads/heasoft-6.15.1/x86_64-unknown-linux-gnu-libc2.5/BUILD_DIR$

---

### Post by drmrgd on 2014-02-08
From just quickly scanning the instructions, my interpretation is that the command you're trying to run is actually two commands, one after the other.  What happens if you run this:

```

export HEADAS=/home/nick/Downloads/heasoft-6.15.1/x86_64-unknown-linux-gnu-libc2.5

```

and then run 

```

. $HEADAS/headas-init.sh

```

---

### Post by carpenter-nicholas on 2014-02-08
Oh my god. I'm retarded. You're my hero. It works perfectly!

---

