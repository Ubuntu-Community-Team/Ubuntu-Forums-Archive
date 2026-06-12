---
title: "Tremulous wont start"
date: 2013-02-13
forum: Gaming &amp; Leisure
---

### Post by Jamie84 on 2013-02-13
Hi    I installed tremulous but the ghame wont start. I see a closed thread with a guy had the same problem. But when i try to type tremulous in the terminal i get the error message &quot; No such file or directory&quot;.  I even type cd /usr/local/games/tremulous and the tremulous but nothing happens.  And when i open that folder and double click the icon nothing happens and no error messages come up.  Can anyone tell me why it wont start?           Thx               Also no idea why my line breaks are not showing

---

### Post by Perfect Storm on 2013-02-13
Try this, it may be missing some libs;

```
ldd /usr/local/games/tremulous/tremulous
```

Also post the outcome of this command to check for binaries and/or scripts to run the game;

```
ls -a /usr/local/games/tremulous
```

---

### Post by Jamie84 on 2013-02-14
On the first comand it said no such file or directory  on the second it gave this  .   base  ChangeLog  GPL        manual.pdf     tremulous.xpm ..  CC    COPYING    .manifest  tremulous.x86  uninstall

---

### Post by Perfect Storm on 2013-02-15
Try with;
```
 sh -c "cd /usr/local/games/tremulous && ./tremulous.x86"
```

---

### Post by Jamie84 on 2013-02-15
hi,  came up with an error " error while loading shared libraries: libSDL-1.2.so.0: cannot open shared object file: No such file or directory"

---

### Post by Jamie84 on 2013-02-15
HI

I downloaded some proprietary libraries to get flash running and now when I double click the icon the screen goes all weird. Like a lot of continuous multi coloured barcodes. It requires a hard reset to get out of.

So im running a fairly fresh install of Ubuntu. Only got firestarter and no script as well as the updates from update manager.

Could I be missing drivers then? 

Thx

Ps posted from mac os which for some reason adds the line breaks where as ubuntu doesn't .

---

### Post by Perfect Storm on 2013-02-15
@ Tremulous

Are you using 23-bit or 64-bit version of ubuntu?
To solve the problem for 32-bit install libsdl.
```
sudo apt-get install libsdl1.2debian
```
On 64-bit system you need to install 32-bit libs to the system:
```
sudo apt-get install ia32-libs
```

I will also suggest when installing games get/use Ubuntu Software Center and get [http://www.playdeb.net/](http://www.playdeb.net/) to get access to a lot of games. Also check [http://www.desura.com/](http://www.desura.com/) and [http://store.steampowered.com/](http://store.steampowered.com/)

@firestarter
You really don't need it, if you're running a home system. I also think firestarter is not maintained for a long time.

@coloured barcode

Which system specs (hardware like video card, ram etc.), and which version of ubuntu do you use? Also do you know the packages you used that made the problem(s)?

---

