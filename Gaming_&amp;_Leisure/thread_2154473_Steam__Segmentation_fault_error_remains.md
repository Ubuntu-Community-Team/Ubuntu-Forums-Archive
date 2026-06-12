---
title: "Steam  Segmentation fault error remains"
date: 2013-06-14
forum: Gaming &amp; Leisure
---

### Post by 7times9 on 2013-06-14
I've recent enjoying playing steam games on Ubuntu, like Half Life 2 and Portal. But now I'm getting an error when I start steam.

I know that [others have had Segmentation fault errors, but those are marked as fixed now]("https://github.com/ValveSoftware/steam-for-linux/issues/1226"). I've tried uninstalling and deleting steam files, then installing again.

This is the error:
```

$ steam
Running Steam on ubuntu 12.04 64-bit
STEAM_RUNTIME is enabled automatically
Installing breakpad exception handler for appid(steam)/version(0_client)
Gen6+ requires Kernel 3.6 or later.
steam: ../../../../../src/mesa/main/context.c:1544: _mesa_make_current: Assertion `newCtx->Version > 0' failed.
ILocalize::AddFile() failed to load file "public/steambootstrapper_english.txt".
[2013-06-15 00:12:55] Startup - updater built Apr 30 2013 10:04:24
/home/tom/.local/share/Steam/steam.sh: line 704:  7797 Segmentation fault      (core dumped) $STEAM_DEBUGGER "$STEAMROOT/$PLATFORM/$STEAMEXE" "$@"
Installing bootstrap /home/tom/.local/share/Steam/bootstrap.tar.xz
Running Steam on ubuntu 12.04 64-bit
STEAM_RUNTIME has been set by the user to: /home/tom/.local/share/Steam/ubuntu12_32/steam-runtime
Installing breakpad exception handler for appid(steam)/version(0_client)
Gen6+ requires Kernel 3.6 or later.
steam: ../../../../../src/mesa/main/context.c:1544: _mesa_make_current: Assertion `newCtx->Version > 0' failed.
ILocalize::AddFile() failed to load file "public/steambootstrapper_english.txt".
[2013-06-15 00:12:56] Startup - updater built Apr 30 2013 10:04:24
/home/tom/.local/share/Steam/steam.sh: line 704:  7884 Segmentation fault      (core dumped) $STEAM_DEBUGGER "$STEAMROOT/$PLATFORM/$STEAMEXE" "$@"



```

It's the same error, whether I do [FONT=courier new]STEAM_RUNTIME=0 steam[/FONT] or [FONT=courier new]STEAM_RUNTIME=1 steam[/FONT]

It may not be related, but I did try [changing desktop environment recently]("http://ubuntuforums.org/showthread.php?t=2154470&p=12691503#post12691503").

Anything else I can try?

---

### Post by 7times9 on 2013-06-16
This seems to be something a bit deeper. Even just [FONT=courier new]glxinfo[/FONT] fails:

```
name of display: :0.0
Gen6+ requires Kernel 3.6 or later.
glxinfo: ../../../../../src/mesa/main/context.c:1544: _mesa_make_current: Assertion `newCtx->Version > 0' failed.
Aborted (core dumped)

```

And the [standard solution]("http://askubuntu.com/a/300315") of [FONT=courier new]sudo apt-get install linux-generic-lts-raring[/FONT] just tells me those are already installed.

---

### Post by user_of_gnomes on 2013-06-16
My Steam occasionally just quits for no apparent reason. How do I get it to output the error message like you did in the terminal?

---

### Post by efflandt on 2013-06-17
To get output errors from steam, just open a terminal window, type **steam**, and hit Enter. However, when it runs properly, the output will be greater than the terminal buffer, so you may want to capture the output to a file with something like:
```
steam > steam.log 2>&1
```That would capture stdout and stderr to a file called steam.log in your current directory (until you exit steam or it crashes).

The first questions if you have issues is what video card/chip do you have and what video drivers are you running?

I have been running steam in 64-bit 12.04 nvidia without issues since before it was released (late beta in January). Except I had to figure out where to put 32-bit flash for steam, and after copying my /home from a failing hard drive I had to use steam to verfify my game files (some textures got messed up) and it fixed those. Steam occasionally asks me to restart it after it downloads updates to itself.

---

### Post by user_of_gnomes on 2013-06-18
Thanks for information!

---

