---
title: "Inspiron 1420 can't start GNOME"
date: 2008-10-10
forum: Dell Ubuntu Support (CLOSED)
---

### Post by Neon8787 on 2008-10-10
Hi everybody.

I know there are already a lot of threads about audio problems, but mine is a little different. Stupidly, I broke the audio after it was already working and now I can't even get into GNOME to post results of tests people may tell me to run from Ubuntu. So at the moment I'm stuck writing down everything by hand....

ANYWAY!! I stupidly decided to try and "update" the sound driver to this one: (the linux one)

[http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PFid=24&Level=4&Conn=3&DownTypeID=3](http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PFid=24&Level=4&Conn=3&DownTypeID=3)

I ran it with sudo in a terminal window and all seemed to go well except for a C compiler error (which, unfortunately, I can't remember) and things seemed fine. I then went to reboot and now get the error:

```
error while loading shared libraries: libasound.so.2: cannot open shared object file: No such file or directory
```

SO!! any ideas??

Already reinstalled linux-sound-base alsa-base and alsa-utils

running ```
alsa -l
``` produced the same error message

Please help me!! Really new to Linux and Ubuntu but wanna make it work.


EDIT: Just checked Dell's website and apparently the in-built audio is SIGMATEL STAC 92XX C-Major HD Audio. Might have tried to install the completely wrong driver lol.

EDIT: Nevermind, giving up.

---

