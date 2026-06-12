---
title: "problem compiling lxdream 0.9.1"
date: 2010-07-08
forum: Gaming &amp; Leisure
---

### Post by beliyyal on 2010-07-08
I been having a problem compiling the latest version of lxdream. Every time I run ./configure, I get this 
```
configure: error: "The OpenGL library (libGL.so) could not be found, but is required."
See `config.log' for more details.
```

So I then went into synaptic, searched "libGL.so" and found "libgl1-mesa-swx11". I marked it for installation, but when I noticed it wanted to remove the packages "libgl1-mesa-glx" and "ubuntu-desktop", I decided against it. I am kinda at a loss here, and was hoping to get some help. Does anyone have an idea as to work this out?

---

### Post by Grishka on 2010-07-08
no compilation is necessary. just use the .deb file. [here](http://www.lxdream.org/download.php).

---

### Post by beliyyal on 2010-07-08
> **Grishka said:**
> no compilation is necessary. just use the .deb file. [here](http://www.lxdream.org/download.php).


The .deb file was the first file I got. I installed it ok and everything, but it just won't run. I get error each time. I am hoping compiling it will fix the problem.

---

### Post by Grishka on 2010-07-08
> **beliyyal said:**
> The .deb file was the first file I got. I installed it ok and everything, but it just won't run. I get error each time. I am hoping compiling it will fix the problem.

what error, buddy? the .deb file works for me. as for compiling, [this](apt://libgl1-mesa-dev) is probably the package you need.

---

### Post by beliyyal on 2010-07-08
> **Grishka said:**
> what error, buddy? the .deb file works for me. as for compiling, [this](apt://libgl1-mesa-dev) is probably the package you need.

Well, I got it compiled and installed ok, finally found the packages I needed, nearly 20 of them. But now it won't run. Every time I try to run it, it starts to open, then closes out quickly. Here is the error I'm getting in terminal
```
lxdream: could not connect to socket
lxdream: No such file or directory
14:36:06 00000000 WARN  Could not initialize LIRC.  LIRC hotkeys will be disabled.
14:36:06 00000000 WARN  Failed to load plugin: '/usr/lib/lxdream/input_lirc.so': Initialization failed
14:36:06 00000000 ERROR Unable to load file 'bios/dcboot.rom': No such file or directory
14:36:06 00000000 WARN  Unable to load file 'bios/dcflash.rom': No such file or directory
Illegal instruction
```

And idea?

---

### Post by Grishka on 2010-07-08
> **beliyyal said:**
> Well, I got it compiled and installed ok, finally found the packages I needed, nearly 20 of them. But now it won't run. Every time I try to run it, it starts to open, then closes out quickly. Here is the error I'm getting in terminal
```
lxdream: could not connect to socket
lxdream: No such file or directory
14:36:06 00000000 WARN  Could not initialize LIRC.  LIRC hotkeys will be disabled.
14:36:06 00000000 WARN  Failed to load plugin: '/usr/lib/lxdream/input_lirc.so': Initialization failed
14:36:06 00000000 ERROR Unable to load file 'bios/dcboot.rom': No such file or directory
14:36:06 00000000 WARN  Unable to load file 'bios/dcflash.rom': No such file or directory
Illegal instruction
```

And idea?

this, obviously, relates to dc bios files, or rather - the lack of thereof. I'm afraid we won't be able to help you with this one - bios files being a taboo subject on these forums. you'd best [look](http://www.lxdream.org/wiki/index.php?title=Getting_Started_%28Linux%29) what the lxdream wiki has to say about the subject.

---

### Post by beliyyal on 2010-07-08
> **Grishka said:**
> this, obviously, relates to dc bios files, or rather - the lack of thereof. I'm afraid we won't be able to help you with this one - bios files being a taboo subject on these forums. you'd best [look](http://www.lxdream.org/wiki/index.php?title=Getting_Started_%28Linux%29) what the lxdream wiki has to say about the subject.

Ahh, I see. Well, I thank you for your help ;).

---

### Post by beliyyal on 2010-07-08
Ok, Suppose hypothetically someone found the theoretical bios, and got it running. They tried to run a game on it, but got this error
```
16:40:05 8C00B8FA WARN  Attempted byte read to missing page: A0600004
WARNING: Application calling GLX 1.3 function "glXCreatePbuffer" when GLX 1.3 is not supported!  This is an application bug!
The program 'lxdream' received an X Window System error.
This probably reflects a bug in the program.
The error was 'BadDrawable (invalid Pixmap or Window parameter)'.
  (Details: serial 11162 error_code 9 request_code 136 minor_code 7)
  (Note to programmers: normally, X errors are reported asynchronously;
   that is, you will receive the error a while after causing it.
   To debug your program, run it with the --sync command line
   option to change this behavior. You can then get a meaningful
   backtrace from your debugger if you break on the gdk_x_error() function.)
```

What would the solution be?

---

### Post by Grishka on 2010-07-09
> **beliyyal said:**
> Ok, Suppose hypothetically someone found the theoretical bios, and got it running. They tried to run a game on it, but got this error
```
16:40:05 8C00B8FA WARN  Attempted byte read to missing page: A0600004
WARNING: Application calling GLX 1.3 function "glXCreatePbuffer" when GLX 1.3 is not supported!  This is an application bug!
The program 'lxdream' received an X Window System error.
This probably reflects a bug in the program.
The error was 'BadDrawable (invalid Pixmap or Window parameter)'.
  (Details: serial 11162 error_code 9 request_code 136 minor_code 7)
  (Note to programmers: normally, X errors are reported asynchronously;
   that is, you will receive the error a while after causing it.
   To debug your program, run it with the --sync command line
   option to change this behavior. You can then get a meaningful
   backtrace from your debugger if you break on the gdk_x_error() function.)
```

What would the solution be?

idk, buddy. maybe this particular game is not supported by the emulator. it may also be an issue with your video card drivers, or perhaps lxdream was compiled with wrong libraries or something. the provided .deb file works fine on my system, perhaps try installing it once again, or try compiling from the scratch, looking carefully for problems with the configure script. also, check your video drivers. if this won't help, perhaps they'll be able to help you at [lxdream forums](http://www.lxdream.org/forums/viewforum.php?f=3&sid=f31bdb9c2eb2ef6f675ea07ae2aa3dc2).

---

