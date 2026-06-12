---
title: "bzflag jitter way too high. can I fix this?"
date: 2009-12-02
forum: Gaming &amp; Leisure
---

### Post by user sam on 2009-12-02
I am totally addicted to the game "bzflag". I would like to play this game on my computer, but I always get kicked for lag and jitter. for about five minutes, everything is normal. then my jitter goes up to about 76, and my lag grows to about 520. I'm getting grumpy because I could successfully play the game in OS X and slackware, just not ubuntu. tried to compile from source, but it won't tell my where it stowed the client. yes i tried "which". 
the default version you get from apt-get is an unstable version, and even if I install an older, more stable version manually I still have the same stupid problem. I use wireless internet. not superspeedy, but it hasn't given me problems like this in the past. I get the same problem in all of the debian-based distros that I've tried as well as pclos. works fine in Open Suse and slackware for some strange reason. well, I'd like my jitter problem solved. I don't know if there's any output you need, but i will post it if you ask.

---

### Post by Perfect Storm on 2009-12-02
I'm not much into multiplayer games so here's a guess; It could be a port that haven't been open? Is the connection fine regarding anything else on Ubuntu?

Have you tried;
```
locate
whereis
```
Normally it would go into /usr/local/ or /usr/share/ if you not specific tells it where you want it installed.

---

### Post by user sam on 2009-12-03
Bzflag is the only program, so far as I can tell, that has trouble with the Internet connection. it is not in /usr/local/bin or /usr/local/games. i have bzadmin in /usr/local/bin, but the game client is not there at all. the one installed via .deb is in /usr/games

---

### Post by user sam on 2009-12-04
I figured out that when i compiled from source, i compiled without the "bzflag client binary!" I'll figure how to compile the client eventually, but for the sake of time it would be nice if someone would tell me what ./configure option i would use.
EDIT: got it. i was missing libsdl-dev. works now. well, it's compiling now anyway. it had better freaking work.

---

