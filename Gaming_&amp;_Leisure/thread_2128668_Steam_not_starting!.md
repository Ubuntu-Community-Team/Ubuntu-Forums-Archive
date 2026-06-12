---
title: "Steam not starting!"
date: 2013-03-23
forum: Gaming &amp; Leisure
---

### Post by Swordeater on 2013-03-23
I have installed steam on ubuntu 12.04, and whenever I try and start steam, I get this error;
```
house@Home-LinuxBox:~$ /usr/bin/steam %URunning Steam on ubuntu 12.04 32-bit
STEAM_RUNTIME is enabled automatically
/home/house/.local/share/Steam/steam.sh: line 704:  5926 Illegal instruction     (core dumped) $STEAM_DEBUGGER "$STEAMROOT/$PLATFORM/$STEAMEXE" "$@"
Installing bootstrap /home/house/.local/share/Steam/bootstrap.tar.xz
Running Steam on ubuntu 12.04 32-bit
STEAM_RUNTIME has been set by the user to: /home/house/.local/share/Steam/ubuntu12_32/steam-runtime
/home/house/.local/share/Steam/steam.sh: line 704:  6044 Illegal instruction     (core dumped) $STEAM_DEBUGGER "$STEAMROOT/$PLATFORM/$STEAMEXE" "$@"
```

---

### Post by HackerFinn on 2013-03-24
Hello. :)
Could you please try running Steam as root?
Greetings. :)

---

### Post by xenall on 2013-07-04
I have the same issue.  I did try to run it as root, but I get a pop up that says - can not run as root

~$ /usr/bin/steam %U
Running Steam on ubuntu 13.04 32-bit
STEAM_RUNTIME is enabled automatically
/.local/share/Steam/steam.sh: line 704:  5033 Illegal instruction     (core dumped) $STEAM_DEBUGGER "$STEAMROOT/$PLATFORM/$STEAMEXE" "$@"
Installing bootstrap /.local/share/Steam/bootstrap.tar.xz
Running Steam on ubuntu 13.04 32-bit
STEAM_RUNTIME has been set by the user to: .local/share/Steam/ubuntu12_32/steam-runtime
/.local/share/Steam/steam.sh: line 704:  5119 Illegal instruction     (core dumped) $STEAM_DEBUGGER "$STEAMROOT/$PLATFORM/$STEAMEXE" "$@"

When I try to excute Steam from the desktop it doesn't do anything.

---

