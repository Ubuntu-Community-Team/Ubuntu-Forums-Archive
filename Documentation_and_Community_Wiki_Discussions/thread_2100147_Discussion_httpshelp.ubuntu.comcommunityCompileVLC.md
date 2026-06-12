---
title: "Discussion: https://help.ubuntu.com/community/CompileVLC"
date: 2012-12-31
forum: Documentation and Community Wiki Discussions
---

### Post by andrew.46 on 2012-12-31
This thread is for discussion of the wiki page:

Compile VLC
[https://help.ubuntu.com/community/CompileVLC](https://help.ubuntu.com/community/CompileVLC)

which deals with the compilation and packaging of the development version of vlc under the latest Ubuntu release. Please feel free to discuss the positive points, negative points of this wiki here and also feel free to edit the wiki page directly with any improvements. Have Fun :)

---

### Post by andrew.46 on 2013-01-01
To get the new year off to a good start I have done a major spring clean of the wiki page:

[LIST=1]
[*]Updated for Quantal Quetzal
[*]FFmpeg version updated to 1.0.1
[*]live555 updated to 2012.09.13, hosted on my own website
[*]libbluray updated to 0.2.3
[*]libaacs updated to 0.5.0
[*]Release version updated to 2.0.5
[/LIST]

All seems to be working well on my Quantal VM, let me know if there are any issues and feel free to alter the wiki yourself :)

---

### Post by andrew.46 on 2013-01-21
I have updated the FFmpeg libraries on the wiki to FFmpeg 1.1.1 "Fire Flower". Compiling and running fine with the current vlc-git:

```

andrew@corinth:~$ **[COLOR="Red"]cvlc --version | head -n 3[/COLOR]**
VLC media player 2.1.0-git Rincewind (revision da60b88)
VLC version 2.1.0-git Rincewind (da60b88)
Compiled by andrew on corinth (Jan 21 2013 18:04:37)
Compiler: gcc version 4.7.2 (Ubuntu/Linaro 4.7.2-2ubuntu1)

```

---

### Post by maffen on 2014-06-19
[SIZE=2][FONT=verdana]Great wiki page. Helped me a lot :)

However, your live555 script doesn't seem to be working any longer. Since I can't edit the wiki page directly here's the fix:

[/FONT][/SIZE]```
[SIZE=2][FONT=verdana]
- wget [http://www.live555.com/liveMedia/public/live.2014.01.24.tar.gz](http://www.live555.com/liveMedia/public/live.2014.01.24.tar.gz) && \
- tar xvf live.2014.01.24.tar.gz && cd live && \
+ wget [http://www.live555.com/liveMedia/public/live555-latest.tar.gz](http://www.live555.com/liveMedia/public/live555-latest.tar.gz) && \
+ tar xvf live555-latest.tar.gz && cd live && \[/FONT][/SIZE]
```

---

### Post by andrew.46 on 2014-06-19
Good to hear the wiki page has been helpful! It is open to all to edit, I am sure if you have a closer look you should be able to undertake this. I will admit that my own efforts with vlc are focused here:


Howto: Compile the development version of vlc under the latest Ubuntu release 
[http://ubuntuforums.org/showthread.php?t=2141949](http://ubuntuforums.org/showthread.php?t=2141949)

which runs for Trusty Tahr now...

---

