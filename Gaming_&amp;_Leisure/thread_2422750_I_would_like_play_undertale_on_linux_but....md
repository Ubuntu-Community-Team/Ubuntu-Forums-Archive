---
title: "I would like play undertale on linux but..."
date: 2019-07-12
forum: Gaming &amp; Leisure
---

### Post by radugw on 2019-07-12
I'm trying to launch Undertale 1.0 version on linux using this way : [https://www.reddit.com/r/linux_gaming/comments/3ywa22/howto_running_undertale_natively_on_linux/](https://www.reddit.com/r/linux_gaming/comments/3ywa22/howto_running_undertale_natively_on_linux/) and I'm using my own assets files and runner because all the scripts download links are dead but when I want to launch the runner file using this command ./runner I have this error :
./runner: error while loading shared libraries: libcrypto.so.1.0.0: cannot open shared object file: No such file on directory
If someone know how to fix this error, please help ! 
PS: I can't run the game using wine or steam and I can only use the 1.0 version of the game.

[IMG]https://i.redd.it/b5lxehclfr931.png[/IMG]

---

### Post by charlieg on 2019-07-12
What version of Ubuntu?

---

### Post by radugw on 2019-07-12
I'm on Ubuntu 18.04.

---

### Post by CatKiller on 2019-07-12
> **radugw said:**
> ./runner: error while loading shared libraries: libcrypto.so.1.0.0: cannot open shared object file: No such file on directory

libcrypto.so.1.0.0 is provided by the libssl1.0.0 package.

---

### Post by oldrocker99 on 2019-07-13
There used to be an installable package called ia32-libs, which would install all the i386 libraries. I'm not sure why it was abandoned. However, ask for an answer and ye shall receive it,

---

### Post by CatKiller on 2019-07-13
> **oldrocker99 said:**
> I'm not sure why it was abandoned. 
Because it was chuffing awful. Just a huge unmaintainable blob. [Multiarch](https://wiki.debian.org/Multiarch) was heaps better as a solution. Killing ia32-libs was a specific goal from somewhere around 12.04.

---

### Post by oldrocker99 on 2019-07-13
> **CatKiller said:**
> Because it was chuffing awful. Just a huge unmaintainable blob. [Multiarch](https://wiki.debian.org/Multiarch) was heaps better as a solution. Killing ia32-libs was a specific goal from somewhere around 12.04.

Ah! Didn't know that :(.

---

