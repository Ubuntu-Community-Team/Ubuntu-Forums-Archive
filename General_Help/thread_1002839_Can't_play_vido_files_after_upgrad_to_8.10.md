---
title: "Can't play vido files after upgrad to 8.10"
date: 2008-12-05
forum: General Help
---

### Post by vedran.omeragic on 2008-12-05
I've just upgraded my laptop to Intrepid, but since then I can't play any video file. Whenever I open some video file, totem player opens, and instanteniously closes. I've tried opening the files with Kaffeine, but I get only black screen, while the audio portion of file is playing...

My graph. card is ATI Radeon x1200. 
Any suggestions how to fix this?

---

### Post by philinux on 2008-12-05
Install totem-xine and remove totem-gstreamer.

And try vlc.

---

### Post by vedran.omeragic on 2008-12-06
I've tried with both vlc and totem running from terminal, and this is the error I get:

in vlc

```
[????????] x11 video output error: X11 request 140.19 failed with error code 11:
 BadAlloc (insufficient resources for operation)
X Error of failed request:  BadAlloc (insufficient resources for operation)
  Major opcode of failed request:  140 (XVideo)
  Minor opcode of failed request:  19 ()
  Serial number of failed request:  83
  Current serial number in output stream:  84

```

And in totem

```
The program 'totem' received an X Window System error.
This probably reflects a bug in the program.
The error was 'BadAlloc (insufficient resources for operation)'.
  (Details: serial 74 error_code 11 request_code 140 minor_code 19)
  (Note to programmers: normally, X errors are reported asynchronously;
   that is, you will receive the error a while after causing it.
   To debug your program, run it with the --sync command line
   option to change this behavior. You can then get a meaningful
   backtrace from your debugger if you break on the gdk_x_error() function.)


```

WTH??

---

### Post by vedran.omeragic on 2008-12-06
OK, after installing ati catalyst control center, I can open video files normally. However, (there's always however), whenever I'm playing any video file, it is tilting, meaning, one second I can see the video normally and the other it's black, and so on. If I watch anything this way, I'll just get an epileptic attack... and as you may have guessed, I'm not really too fond of that.. :) 
Anyway, what could cause this and what can fix it!?!?

EDIT:
I've just turned visual effects from Normal to None, and it seems to have stopped it, but I'd rather have those working... :(

---

