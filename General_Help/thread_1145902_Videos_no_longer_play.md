---
title: "Videos no longer play"
date: 2009-05-02
forum: General Help
---

### Post by mishathegoat on 2009-05-02
Hey everyone,

My video just randomly stopped working. I can't play any videos with mplayer or vlc or any video player I download. I downloaded a couple KDE media players but they will only play the audio. When I begin to play a video in mplayer or vlc the window closes by itself. Its weird be cause the icon of the video I'm about to play is a screenshot/preview/icon of the movie.. But the players close down as soon as I try to play the video.

I've tried WMV files as well as DivX Avi files.. 


EeePC 1000he Netbook
1.66 Ghz Dual-core
1G RAM
Ubuntu 9.04 - updates all installed

Any ideas?

---

### Post by mishathegoat on 2009-05-03
Bump

---

### Post by BslBryan on 2009-05-03
Are you sure it was random?  Did you do *anything* at all that might have triggered it?

---

### Post by mishathegoat on 2009-05-03
Well I guess it started after I started playing videos with my laptop hooked up to my monitor... Or maybe I installed something like some codecs I'm not sure I can't remember..

---

### Post by MaxIBoy on 2009-05-03
Did you update anything recently?

Are you able to turn the desktop graphic effects on?

Try running a media player from the terminal, trying to watch a video on it, and then seeing if any error messages are displayed to the terminal. If so, copy and paste them into a post and we'll have a look at them.

---

### Post by mishathegoat on 2009-05-03
This is the output for vlc

```
[00000001] main libvlc: Running vlc with the default interface. Use 'cvlc' to use vlc without interface.
[00000452] a52 decoder: A/52 channels:2 samplerate:48000 bitrate:192000
[????????] x11 video output error: X11 request 132.19 failed with error code 11:
 BadAlloc (insufficient resources for operation)
X Error of failed request:  BadAlloc (insufficient resources for operation)
  Major opcode of failed request:  132 (XVideo)
  Minor opcode of failed request:  19 ()
  Serial number of failed request:  81
  Current serial number in output stream:  82
```

This is from totem

```
/var/lib/python-support/python2.6/gdata/tlslite/utils/cryptomath.py:9: DeprecationWarning: the sha module is deprecated; use the hashlib module instead
  import sha
The program 'totem' received an X Window System error.
This probably reflects a bug in the program.
The error was 'BadAlloc (insufficient resources for operation)'.
  (Details: serial 133 error_code 11 request_code 132 minor_code 19)
  (Note to programmers: normally, X errors are reported asynchronously;
   that is, you will receive the error a while after causing it.
   To debug your program, run it with the --sync command line
   option to change this behavior. You can then get a meaningful
   backtrace from your debugger if you break on the gdk_x_error() function.)
```

---

### Post by mishathegoat on 2009-05-03
Ok, I've also found that music/videos will play in totem/mplayer/whatever when it is minimized.. But if you maximize the window it will close itself

---

### Post by mishathegoat on 2009-05-04
Bump, I'm thinking I may just re-install Ubuntu..

---

### Post by ikacer on 2009-05-04
maybe it has something to do with the x11 video output. What happens if you try to use the xv video driver instead? If you can identify the program causing the error, you can probably fix it by just reinstalling that program. also, you might want to take a look at this thread: [ [all variants] Comprehensive Multimedia & Video Howto ]("http://ubuntuforums.org/showthread.php?t=766683")

---

