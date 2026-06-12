---
title: "znes"
date: 2005-02-10
forum: Gaming &amp; Leisure
---

### Post by miho on 2005-02-10
I'm trying to install znes on my pc with ubuntu linux. I'm having a problem installing it. Can something give me the command/s to install it?

---

### Post by Adrenal on 2005-02-10
sudo apt-get install zsnes

---

### Post by Daniel G. Taylor on 2005-02-10
[QUOTE=Adrenal]sudo apt-get install zsnes[/QUOTE]
 What repository is that in?

---

### Post by adbak on 2005-02-10
[QUOTE=Daniel G. Taylor]What repository is that in?[/QUOTE]
 [http://www.everyvideogame.com/nintendo_game_list.htm](http://www.everyvideogame.com/nintendo_game_list.htm)

Play any Nintendo and Sega game.

---

### Post by pagefault on 2005-02-10
I would be interested to know if there is a ZSNES package for ubuntu. I can't find any in the hoary repository. Would be willing to create one otherwise.

---

### Post by Wertigon on 2005-02-10
[QUOTE=pagefault]I would be interested to know if there is a ZSNES package for ubuntu. I can't find any in the hoary repository. Would be willing to create one otherwise.[/QUOTE]

Check Universe. It's there. Else the Debian repositories work great, and it's quite easy to compile yourself.

In fact, I reccommend you to compile it yourself, since the repository version is 1.36 and the latest one is 1.42, and it's a fricken' huge difference between the two. Check out [www.zsnes.com](www.zsnes.com) for more info.

---

### Post by pagefault on 2005-02-10
Ah well I work on the ZSNES project which is why I asked :) I recently switched from gentoo so I am still getting used to the whole apt thing. :)

---

### Post by valadil on 2005-02-10
zsnes is in apt for me.  If it's not in universe try multiverse.

If you're on an amd64 good luck getting zsnes to run.  I hear tell it's programmed in assembly.  That would explain why theres no debian package of it under amd64.  You can run it in a 32 bit chroot though.

---

### Post by pagefault on 2005-02-10
[QUOTE=valadil]zsnes is in apt for me.  If it's not in universe try multiverse.

If you're on an amd64 good luck getting zsnes to run.  I hear tell it's programmed in assembly.  That would explain why theres no debian package of it under amd64.  You can run it in a 32 bit chroot though.[/QUOTE]

We are currently looking for ways to support 64-bit right now. Currently we use NASM which doesn't support the option of 64-bit object files so we are kind of stuck right now. However we are trying to get it working with YASM which is NASM compatible and will produce 64-bit object files.

---

### Post by Wertigon on 2005-02-10
[QUOTE=pagefault]Ah well I work on the ZSNES project which is why I asked :) I recently switched from gentoo so I am still getting used to the whole apt thing. :)[/QUOTE]
 Ah, right. Should've recognized the name, too much caffeine I guess. :)

You really do make a killer app, it's one of the only things left that's preventing me from getting a Mac. Stupid unportable ASM... ;)

---

### Post by cborga1985 on 2006-10-07
> **Wertigon said:**
> Ah, right. Should've recognized the name, too much caffeine I guess. :)

You really do make a killer app, it's one of the only things left that's preventing me from getting a Mac. Stupid unportable ASM... ;)
has anybody else used a i386 package and used this to install it.
```
sudo dpkg -i --force-architecture
```
The package I built works doing this.

---

