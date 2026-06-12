---
title: "Super Mario Clone SMC won't run?"
date: 2006-06-06
forum: Gaming &amp; Leisure
---

### Post by mark2741 on 2006-06-06
I downloaded the rpm and converted using alien (what a cool tool!). I then installed SMC using the package manager. To my pleasant surprise, once installation was complete I checked the Applications > Games menu and SMC was in there! But alas, when I click on it, nothing happens. It won't run.

So I CD'd via a terminal to the /usr/local/games/SMC directory and then type in:

smc

But I get a "not a valid command" or something liek that.

I really would like to play this game but I can't get it to run. I have every package with SDL in the name installed so that can't be it : )  Any ideas?

---

### Post by bluevoodoo1 on 2006-06-06
[QUOTE=mark2741]I downloaded the rpm and converted using alien (what a cool tool!). I then installed SMC using the package manager. To my pleasant surprise, once installation was complete I checked the Applications > Games menu and SMC was in there! But alas, when I click on it, nothing happens. It won't run.

So I CD'd via a terminal to the /usr/local/games/SMC directory and then type in:

smc

But I get a "not a valid command" or something liek that.

I really would like to play this game but I can't get it to run. I have every package with SDL in the name installed so that can't be it : )  Any ideas?[/QUOTE]

I just downloaded it to see if I could help. Running "smc" doesn't work either, but
/usr/local/games/SMC/smc gives me an "error loading shared libraries" which *might* be a good sign.... for you.

---

### Post by charlieg on 2006-06-06
[QUOTE=mark2741]So I CD'd via a terminal to the /usr/local/games/SMC directory and then type in:

smc

But I get a "not a valid command" or something liek that.[/QUOTE]
Try ./smc as standalone commands just look in the default paths, not the current one so you need the ./ to force it to try the current path:
```
 ~$ cd /usr/local/games/SMC
SMC$ ./smc
```

---

### Post by KillerBOB on 2006-06-06
Hi! I "aliened" the .rpm just as you did. However I assume this error is the same that you are getting when trying to start the game:
```
oaolsson@blacklodge:~$ smc.x
./smc: error while loading shared libraries: libSDL_gfx.so.13: cannot open shared object file: No such file or directory
```

By adding this symlink the game starts and runs quite well:

```
sudo ln -s /usr/lib/libSDL_gfx.so.4.9.0 /usr/lib/libSDL_gfx.so.13
```

So far I'm unsuccessful in compiling version 0.9.8 from scratch, but this 0.9.6 .rpm seems tu run ok now.

Hope this helps

---

### Post by eqisow on 2006-06-06
Unless you particularly like SMC, you alwats install ZSNES and play Super Nintendo games. :)

There are plenty of other emulators available as well.

---

### Post by mark2741 on 2006-06-06
Thanks guys. The symbolic link thing worked but then 2 minutes into the game it crashed. I didn't realize there was a SNES emulator - makes sense to just go with that I guess. Thanks again.

---

### Post by charlieg on 2006-06-07
No, it doesn't make sense to go to a SNES emulator.

SMC is Free, it has higher res graphics, and is a community game.  Get involved!  Help it develop, even by just playing it.

---

### Post by mark2741 on 2006-06-07
I'm not a programmer, and the game doesn't work on Ubuntu (my chosen OS) in a stable manner. How can I fix it/play it?

---

### Post by DoktorSeven on 2006-06-07
There's always [SuperTux](http://supertux.berlios.de/)...

---

### Post by charlieg on 2006-06-07
[QUOTE=mark2741]I'm not a programmer, and the game doesn't work on Ubuntu (my chosen OS) in a stable manner. How can I fix it/play it?[/QUOTE]
Maybe you can't fix it directly but you CAN report your problems to the SMC developers.  They have (IIRC) a forum on [http://www.secretmaryo.org](http://www.secretmaryo.org) so you can help them out by letting them know any issues you are having so they can fix them.  Then the next release will probably run well for you and you will get to play the game properly then!

---

