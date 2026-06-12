---
title: "issue with playing wmv/mpg files"
date: 2009-05-12
forum: General Help
---

### Post by WinterMadness on 2009-05-12
both totem and vlc close when they goto play the video, I installed ffmpeg and such.
I tried opening it in the terminal to see whats up, heres what I got


joe@joe-desktop:~/Videos$ totem '/home/joe/Videos/video.wmv' 
/var/lib/python-support/python2.6/gdata/tlslite/utils/cryptomath.py:9: DeprecationWarning: the sha module is deprecated; use the hashlib module instead
  import sha
The program 'totem' received an X Window System error.
This probably reflects a bug in the program.
The error was 'BadAlloc (insufficient resources for operation)'.
  (Details: serial 94 error_code 11 request_code 132 minor_code 19)
  (Note to programmers: normally, X errors are reported asynchronously;
   that is, you will receive the error a while after causing it.
   To debug your program, run it with the --sync command line
   option to change this behavior. You can then get a meaningful
   backtrace from your debugger if you break on the gdk_x_error() function.)

---

### Post by WinterMadness on 2009-05-12
Bumpity

---

### Post by bumanie on 2009-05-12
Go to [here]("https://help.ubuntu.com/community/Medibuntu") and follow the instructions for your ubuntu version. You are most likely missing multi-media codecs etc.

---

### Post by WinterMadness on 2009-05-12
that cant be it because when i actually remove the codecs needed, only then does totem try and search for them. 

The program 'totem' received an X Window System error.
This probably reflects a bug in the program.
The error was 'BadAlloc (insufficient resources for operation)'.
(Details: serial 94 error_code 11 request_code 132 minor_code 19)

looks like the codecs arent getting a long with something else.

---

### Post by WinterMadness on 2009-05-12
anyone?

---

