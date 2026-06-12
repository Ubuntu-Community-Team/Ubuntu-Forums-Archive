---
title: "Steam won't start on Ubuntu 14.04.1"
date: 2014-08-29
forum: Gaming &amp; Leisure
---

### Post by stefanmarkic on 2014-08-29
When I click on the icon from the Launcher, nothing happens. When I enter 'steam' in Terminal, I get this:

```
steam
Running Steam on ubuntu 14.04 64-bit
STEAM_RUNTIME is enabled automatically
Installing breakpad exception handler for appid(steam)/version(0_client)
Uploading dump (out-of-process) [proxy '']
/tmp/dumps/crash_20140829154109_1.dmp
Finished uploading minidump (out-of-process): success = no
error: libcurl.so: cannot open shared object file: No such file or directory
/home/stefan/.local/share/Steam/steam.sh: line 730:  6206 Segmentation fault      (core dumped) $STEAM_DEBUGGER "$STEAMROOT/$STEAMEXEPATH" "$@"
mv: cannot stat &#8216;/home/stefan/.steam/registry.vdf&#8217;: No such file or directory
Installing bootstrap /home/stefan/.local/share/Steam/bootstrap.tar.xz
Reset complete!
Restarting Steam by request...
Running Steam on ubuntu 14.04 64-bit
STEAM_RUNTIME has been set by the user to: /home/stefan/.local/share/Steam/ubuntu12_32/steam-runtime
Installing breakpad exception handler for appid(steam)/version(0_client)
Uploading dump (out-of-process) [proxy '']
/tmp/dumps/crash_20140829154110_1.dmp
Finished uploading minidump (out-of-process): success = no
error: libcurl.so: cannot open shared object file: No such file or directory
/home/stefan/.local/share/Steam/steam.sh: line 730:  6332 Segmentation fault      (core dumped) $STEAM_DEBUGGER "$STEAMROOT/$STEAMEXEPATH" "$@"
```

What to do? :( I installed Steam from the Ubuntu Software Center.

---

### Post by belarrius on 2014-08-29
Hi!

You want ia32-libs i think.

sudo apt-get install ia32-libs

---

### Post by oldrocker99 on 2014-08-30
14.04 no longer has ia32-libs. 32-bit libraries are still available, so, according to the message you got, try
```
sudo apt-get install libcurl:i386
```

If you're running any 32-bit program, and you get a missing library error, remember the name of the library (without the .so suffix) and place a :i386 after the library name, as I show above.

If it worked, please post here. If it didn't, by all means post here.

This is nowhere as simple as installing the old ia32-libs, but it's what you have to do to run 32-bit programs which complain of missing libraries

---

### Post by R33D3M33R on 2014-08-30
Try installing from [http://store.steampowered.com/about/](http://store.steampowered.com/about/) and it might fix missing dependencies itself.

---

### Post by stefanmarkic on 2014-09-01
> **oldrocker99 said:**
> 14.04 no longer has ia32-libs. 32-bit libraries are still available, so, according to the message you got, try
```
sudo apt-get install libcurl:i386
```

when I try to isntall it, I get this message:

```
Reading package lists... DoneBuilding dependency tree       
Reading state information... Done
E: Unable to locate package libcurl
```

---

### Post by stefanmarkic on 2014-09-01
> **R33D3M33R said:**
> Try installing from [http://store.steampowered.com/about/](http://store.steampowered.com/about/) and it might fix missing dependencies itself.

Exactly the same package is located in the Ubuntu Software Center.

---

### Post by belarrius on 2014-09-01
Hmmm

Try:

```

sudo apt-get install libcurl3 libcurl3-gnutls libcurl4-openssl-dev

```

:D

---

### Post by oldrocker99 on 2014-09-01
I didn't look up the proper name for libcurl, my bad. 

When you need to find the exact name of a file (in this example, libcurl):
```
apt-cache search libcurl
```


You can also pipe the output to grep (another example):
```
apt-cache search chrome | grep google
```

Since the search results in a number of files which contain 'chrome' in their title or description, piping through grep and looking for files with 'google' in the name limits the result just to files with that word in their name ot description.

---

### Post by vpiercy on 2014-09-01
So Steam won't work on the latest Ubuntu? 

Should I install an earlier version of Ubuntu? Steam worked with 12.04 LTS.

0--------------------------0

UPDATE: I re-installed Steam via the steam_latest.deb as suggested in the post above (but identical file in the Ubuntu Software Store) and I ran the > sudo apt-get install libcurl3 libcurl3-gnutls libcurl4-openssl-dev in terminal. 

Then I tried to run a Steam shortcut for a game, got the usual "Fatal Error: Failed to load steamui.so" when I try to launch a Steam game in Xubuntu 14.04. Then I clicked the Steam shortcut, got the same "Fatal Error" msg., but then Steam updated ( a big update)! And now I have a login window.

---

### Post by R33D3M33R on 2014-09-02
> **stefanmarkic said:**
> Exactly the same package is located in the Ubuntu Software Center.


This is not true. The packages are different in almost every file and even have different lists of depends:

```
Package: steam
Version: 1:1.0.0.45-1ubuntu1
Architecture: i386
Maintainer: Ubuntu Developers <ubuntu-devel-discuss@lists.ubuntu.com>
Installed-Size: 2731
Pre-Depends: debconf, multiarch-support
Depends: debconf (>= 0.5) | debconf-2.0, libc6 (>= 2.12), libstdc++6 (>= 4.3), libx11-6, xz-utils, libgl1-mesa-dri, libgl1-mesa-glx, libtxc-dxtn-s2tc0, xterm | x-terminal-emulator
Recommends: zenity, fonts-liberation
Section: non-free/games
Priority: extra

```

```

Package: steam-launcher
Source: steam
Version: 1.0.0.49
Architecture: all
Maintainer: Valve Corporation <linux@steampowered.com>
Installed-Size: 2271
Depends: python, curl, libc6 (>= 2.15), python-apt, xterm | gnome-terminal | konsole, xz-utils, zenity
Recommends: jockey-common
Breaks: steam64
Replaces: steam, steam64
Section: games
Priority: optional

```

As you can see, steam_latest.deb depends on curl and it would thus be downloaded and installed.

---

### Post by c-mandellscott on 2014-09-02
I had the same issue. I uninstalled fglrx and Steam, used the built-in graphics drivers, rebooted, reinstalled steam, and then reinstalled GPU drivers. It works perfectly fine now.

---

### Post by stefanmarkic on 2014-09-02
I removed, purged and manually deleted everything related to Steam.
I switched graphic card drivers from proprietary to the open source ones.
Installed Steam again.
Now able to run it.
Switched to proprietary drivers again.
Started Steam again and I'm able to run it.
I couldn't start Dota 2 because I got some graphics related error messages.
Fixed them all.
Dota 2 runs like ****.
Deleted everything.

Anyway, thanks everyone for helping out.

---

### Post by dora5 on 2015-03-08
I don't know what's different about the version of Steam in the software center; from my already considerable experience with it they don't necessarily update it between versions of Ubuntu.    It hung on install due to a "known bug".   But when I downloaded the package from the Steam web site it installed fine.   It did download an update.   

I haven't tried to restart it yet.  I'm trying to find the bug report page so I can let people know it's only that they can't install Steam from the software center in Ubuntu 14.04.   However, to be on the safe side, I followed the above instructions for both ia32-libs, and libcurl:i386, and both worked perfectly. 

 I am running 32 bit Ubuntu 14.04.   I have a 64 bit system, but I want to run some of my 32 bit Windows software.  Support seems to be dissolving for 32 bit linux everywhere.

---

### Post by dora5 on 2015-03-08
Don't know if I'll be installing any games though - nothing on Steam appeals to me.  However what I really want is for my family to be able to use Ubuntu, and the kids love Steam.

---

### Post by oldrocker99 on 2015-03-08
Steam is not 100% games. [http://store.steampowered.com/tag/en/Animation%20%26%20Modeling/](http://store.steampowered.com/tag/en/Animation%20%26%20Modeling/) shows just some of the software available.

---

### Post by lorenzo17 on 2015-04-10
Hello,

Had the same issue after installing Steam.
When clicking the Steam icon it would do nothing.

This is how i solved it:

Go to terminal, type steam
It will prompt you to install the required dependencies, which are many.

> 
Package libgl1-mesa-dri:i386 
Package libgl1-mesa-glx:i386
Package libc6:i386



The rest of the process is automatic, for which i am thankful.

Also had an issue with the login.
A window told me that steam could not connect to the internet.
The issue was solved by typing              steam -tcp

---

