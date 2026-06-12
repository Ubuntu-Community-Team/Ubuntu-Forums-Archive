---
title: "VLC segfaults suddenly, worked yesterday"
date: 2006-09-12
forum: Desktop Environments
---

### Post by KalasMannen on 2006-09-12
Hi!

I have a problem with my VLC. When i try to start it nothing happoends, i try to run it through the terminal, but ge segmentation fault. This is the output from "vlc -vvv" (very very verbose?)

```
VLC media player 0.8.5 Janus
[00000001] main vlc debug: opening config file /home/kalasmannen/.vlc/vlcrc
[00000001] main vlc warning: config file /home/kalasmannen/.vlc/vlcrc does not exist yet
[00000001] main vlc debug: checking builtin modules
[00000001] main vlc debug: checking plugin modules
[00000001] main vlc debug: loading plugins cache file /home/kalasmannen/.vlc/cache/plugins-04041e.dat
[00000001] main vlc debug: recursively browsing `modules'
[00000001] main vlc debug: recursively browsing `/usr/lib/vlc'
[00000001] main vlc debug: recursively browsing `plugins'
[00000001] main vlc debug: module bank initialized, found 215 modules
[00000001] main vlc debug: opening config file /home/kalasmannen/.vlc/vlcrc
[00000001] main vlc warning: config file /home/kalasmannen/.vlc/vlcrc does not exist yet
[00000001] main vlc debug: CPU has capabilities 486 586 MMX MMXEXT SSE SSE2 FPU 
[00000001] main vlc debug: looking for memcpy module: 1 candidate
[00000001] main vlc debug: using memcpy module "memcpy"
[00000277] main playlist debug: waiting for thread completion
[00000277] main playlist debug: thread 16386 (playlist) created at priority 0 (playlist/playlist.c:184)
[00000278] main private debug: waiting for thread completion
[00000278] main private debug: thread 32771 (preparser) created at priority 0 (playlist/playlist.c:210)
[00000279] main interface debug: looking for interface module: 1 candidate
[00000279] main interface debug: using interface module "hotkeys"
[00000279] main interface debug: thread 49156 (interface) created at priority 0 (interface/interface.c:231)
[00000281] main interface debug: looking for interface module: 1 candidate
[00000281] main interface debug: using interface module "screensaver"
[00000281] main interface debug: thread 65541 (interface) created at priority 0 (interface/interface.c:231)
[00000283] main interface debug: looking for interface module: 4 candidates
[00000283] main interface debug: using interface module "wxwidgets"
[00000283] main interface debug: thread 81926 (manager) created at priority 0 (interface/interface.c:216)
Segmentation fault

```

NOTE: I changed the last line from swedish to english, in case anyone wounders.

Anyone knows what might cause this?

---

### Post by Ramses de Norre on 2006-09-12
I have segfaults sometimes too with some apps, and mostly this means there is something f***** up in my memory and a reboot fixes this. It doesn't happen very often but it does..

---

### Post by KalasMannen on 2006-09-12
I'll try rebooting soon, kind of wierd though, since i've never experienced anything like this before.. :frown: 

I've tried to run both the "official" release from VLCs download page (0.8.4) and the nigtlies for Dapper (0.8.5).

But i'll do as you said, reboot and see if that solves it. :wink:

---

### Post by KalasMannen on 2006-09-12
Okay, so now i've tried to reboot three times, and it still segfaults, what can possibly be wrong? I try to think back on what i did that very day that it last worked. The only thing i can remember is running a systemupdate.. I'll try and see if i get the same problem on my other computers this weekend..

---

