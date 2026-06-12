---
title: "Totem freeze"
date: 2005-04-14
forum: Desktop Environments
---

### Post by Haiyadragon on 2005-04-14
When I start Totem it freezes (doesn't respond). I've tried both Xine and Gstreamer. I've tried to run it with sudo. The weird thing is that it played fine last night. I'm guessing it's some kind of conflict. Can anybody help me with this?

---

### Post by FX on 2005-05-24
I wish someone would answer cause I am having the same problem.

---

### Post by RastaMahata on 2005-05-24
did you install some packages recently? What version of totem are you using?
Run totem --debug and post the results here.

---

### Post by GriMsb on 2005-05-26
I am using totem-xine 1.1.1 on Ubuntu 5.04.  When I try to open "file.wma", it sounds for 1 or 2 seconds, and then totem shuts down and exits.  My machine is a Dell Inspiron 8500 with RAM 512MB, and NVidia Geforce4 4200 Go.
I have ran "totem --debug file.wma" and that is the information:

The program 'totem' received an X Window System error.
This probably reflects a bug in the program.
The error was 'BadAlloc (insufficient resources for operation)'.
  (Details: serial 87 error_code 11 request_code 142 minor_code 19)
  (Note to programmers: normally, X errors are reported asynchronously;
   that is, you will receive the error a while after causing it.
   To debug your program, run it with the --sync command line
   option to change this behavior. You can then get a meaningful
   backtrace from your debugger if you break on the gdk_x_error() function.)
 ---->(better english than me, ;))

I have programmed C many years with msdos and windows, and I do not know how to start to debug Linux.  I am a newbie! Where are the tools?  Perhaps this is too hard to start? What can I do?
Thanks a lot.
---------------------------------------------------------------------------------------------

My Solution:
I had my screen running, so I thought that my video drivers was working, but it is wrong.  I must install the nvidia drivers (thanks to [http://ubuntuguide.org)](http://ubuntuguide.org)).  When I install them, totem works fine.

---

### Post by waft on 2005-05-27
I have problem with totem. It does not start and this error appears:

```
Totem could not startup.
ALSA device "default" is already in use by another program.
```

---

### Post by eldude on 2005-09-06
With me totem causes to freeze up my total system.
This happens from the beginning. Aswel as i tried playing mp3-list (m3u or something like that ;-) ) as when i played mpeg or avi files.
After that i installed the totem/xine and it still freezes my distribution. Then i added all possible codecs from the 'main' ubuntu repository and from the 'universe multiverse restricted' (i know that the last one can cause problems) but the problem remains. I have to do a cold start when it happens that's a no go.
When i'm @ home tonight i will put the debug messages online.

---

### Post by eldude on 2005-09-07
totem --debug freezes ubuntu and i have to do a cold start.

Audio plays well with xmms and rhythmbox (i removed all oss packages and set all the settings to alsa)

The main problem stays, video. 

When i test the different settings with the multimedia system selector, my system always freezes and i have to do a cold start.

I already followed the guidelines from [http://www.ubuntuguide.org/](http://www.ubuntuguide.org/), i thought maybe something was missing. 

Has anybody an idea what i can do to solve this. I'm still a newbie ...

tnx in advance

---

