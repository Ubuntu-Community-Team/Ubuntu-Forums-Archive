---
title: "Can't Install libav-tools"
date: 2012-05-30
forum: Desktop Environments
---

### Post by Acharn on 2012-05-30
I have a video clip of a song I really, really want to include in my music library. I figured it would be easy to convert to .mp3 -- I've done it before -- but I discovered ffmpeg isn't installed in Precise Pngolin. So I tried to install it. Then I found out I'm supposed to use avconv instead. OK, it's not installed either.
```

roger@roger-Aspire-M1610:~$ avconv
The program 'avconv' is currently not installed.  You can install it by typing:
sudo apt-get install libav-tools
roger@roger-Aspire-M1610:~$ sudo apt-get install libav-tools
[sudo] password for roger: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package libav-tools is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source

E: Package 'libav-tools' has no installation candidate

```
I have all the ppa's installed, including ubuntu-restricted. What should I try next?

---

### Post by Acharn on 2012-05-31
Oh, dear. Stumbled on the answer myself. I switched my Software Sources to download from a different server and everything installed fine.

---

