---
title: "Mupen64plus won't load"
date: 2009-07-07
forum: Gaming &amp; Leisure
---

### Post by Beware The Birchmen on 2009-07-07
Hi
I get "mupen64plus the core thread recieved a SIGSEGV signal" when I try and run anything.

I saw this thread [http://art.ubuntuforums.org/showthread.php?p=7411356](http://art.ubuntuforums.org/showthread.php?p=7411356)

where the last post says

"For anyone googling this, I can confirm that both running Mupen as root and, preferably, a chown on ~/.mupen64plus solved the problem. Thanks for the hint!"

But I'm not sure what it means. Can someone help me out?

---

### Post by bear24rw on 2009-07-07
did you compile from the svn?

---

### Post by Beware The Birchmen on 2009-07-07
Hi thanks for the reply
I downloaded the zipped file from the googlecode website I think it is a precompiled file. The program runs but when I goto load a rom it gives that error.

---

### Post by bear24rw on 2009-07-07
i would try compiling from the svn, there are instuctions in the wiki section. i've compiled mupen on a few computers and it always works great try to get the svn version compiled...

[http://code.google.com/p/mupen64plus/wiki/CompilingFromSVN](http://code.google.com/p/mupen64plus/wiki/CompilingFromSVN)

---

### Post by Beware The Birchmen on 2009-07-07
seems the same. did you have to do the chown command they suggested in that other thread to get it working on your computer? not exactly sure what they're saying to do to make it work.

---

### Post by bear24rw on 2009-07-07
no i dont remember ever having to do a chown, cd into the directory the binary is in and post the output of

ls -l

thats an L

---

### Post by Beware The Birchmen on 2009-07-07
total 1280
drwxr-xr-x 2 birchmen birchmen   4096 2009-01-04 13:50 config
drwxr-xr-x 2 birchmen birchmen   4096 2009-01-04 13:50 doc
drwxr-xr-x 2 birchmen birchmen   4096 2009-01-04 13:50 fonts
drwxr-xr-x 5 birchmen birchmen   4096 2009-01-04 13:50 icons
-rwxr-xr-x 1 birchmen birchmen   3502 2009-01-04 13:50 install.sh
drwxr-xr-x 2 birchmen birchmen   4096 2009-01-04 13:50 lang
-rw-r--r-- 1 birchmen birchmen   2313 2009-01-04 13:50 LICENSES
-rwxr-xr-x 1 birchmen birchmen 808972 2009-01-04 13:50 mupen64plus
-rw-r--r-- 1 birchmen birchmen    273 2009-01-04 13:50 mupen64plus.desktop
-rw-r--r-- 1 birchmen birchmen 403362 2009-01-04 13:50 mupen64plus.ini
drwxr-xr-x 2 birchmen birchmen   4096 2009-01-04 13:50 plugins
-rw-r--r-- 1 birchmen birchmen   9487 2009-01-04 13:50 README
-rw-r--r-- 1 birchmen birchmen  25659 2009-01-04 13:50 RELEASE
drwxr-xr-x 2 birchmen birchmen   4096 2009-07-07 13:18 roms
-rwxr-xr-x 1 birchmen birchmen   2164 2009-01-04 13:50 uninstall.sh

was the output of ls -l in the directory

---

### Post by bear24rw on 2009-07-07
looks fine you can try running it as root like that other thread suggests
```

sudo ./mupen64plus
```

---

### Post by Beware The Birchmen on 2009-07-07
hmm. unfortunately that didn't work either.

---

### Post by ShadowTek on 2009-07-07
Mupen64plus doesn't have very good analog control configuration options, which made it useless for me, so I suggest forgetting about Mupen64plus, at least until it's updated.

I ended up using the Windows executable for 1964 with Wine, and it worked pretty well on the games I tried.

---

### Post by bear24rw on 2009-07-08
> **ShadowTek said:**
> Mupen64 doesn't have very good analog control configuration options, which made it useless for me, so I suggest forgetting about Mupen64, at least until it's updated.

I ended up using the Windows executable for 1964 with Wine, and it worked pretty well on the games I tried.

mupen64 is old, mupen64**plus** is excellent. it even works with wireless xbox controller in ubuntu plug and play

---

### Post by BoyOfDestiny on 2009-07-08
Okay I haven't run into this problem, so not sure if this will help solve your issue... I'm running mupen64plus,. built from source, but just the one for download, not the svn version.

Don't run emulators as root, that's just bad advice all around. If there was a permission problem (requiring chown) it's probably due to that. So I suggest, delete the .mupen64plus folder in your home (it's hidden so ctrl + h to view) 

Run the emulator from terminal (no sudo) and look for errors.

EDIT: Looked at that other thread, a bunch of errors spitting out about the rice video plugin and nvidia for that person... Run mup3n64plus, go to Options -> Configure -> Plugins, try changing it to another plugin. It could just be a problem with your video driver and that plugin...

---

### Post by ShadowTek on 2009-07-08
> **bear24rw said:**
> mupen64 is old, mupen64**plus** is excellent. it even works with wireless xbox controller in ubuntu plug and play
Oh, that's what I meant. I *was* talking about Mupen64plus, the last version of which I tried was v1.5.

The analog control issue that I'm referring to is discussed here:
[http://code.google.com/p/mupen64plus/issues/detail?id=67&colspec=ID%20Type%20Component%20Status%20Priority%20Stars%20Milestone%20Owner%20Summary](http://code.google.com/p/mupen64plus/issues/detail?id=67&colspec=ID%20Type%20Component%20Status%20Priority%20Stars%20Milestone%20Owner%20Summary)

---

### Post by Beware The Birchmen on 2009-07-13
> **BoyOfDestiny said:**
> Okay I haven't run into this problem, so not sure if this will help solve your issue... I'm running mupen64plus,. built from source, but just the one for download, not the svn version.

Don't run emulators as root, that's just bad advice all around. If there was a permission problem (requiring chown) it's probably due to that. So I suggest, delete the .mupen64plus folder in your home (it's hidden so ctrl + h to view) 

Run the emulator from terminal (no sudo) and look for errors.

EDIT: Looked at that other thread, a bunch of errors spitting out about the rice video plugin and nvidia for that person... Run mup3n64plus, go to Options -> Configure -> Plugins, try changing it to another plugin. It could just be a problem with your video driver and that plugin...


Thanks for the replies. Have I messed up my Ubuntu instalation by running it as root? Could it have damaged it?

---

### Post by BoyOfDestiny on 2009-07-13
> **Beware The Birchmen said:**
> Thanks for the replies. Have I messed up my Ubuntu instalation by running it as root? Could it have damaged it?

Your installation should be fine, worst case there is a .folder sitting in /root that isn't needed

---

