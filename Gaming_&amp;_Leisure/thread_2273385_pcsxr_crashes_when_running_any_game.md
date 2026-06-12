---
title: "pcsxr crashes when running any game"
date: 2015-04-12
forum: Gaming &amp; Leisure
---

### Post by carega on 2015-04-12
Hello again,

I recently upgraded to Ubuntu 14.04 and pcsxr is not running correctly. Whenever I try to run any game I have it crashes and the Terminal shows the following message:

```
The program 'pcsx' received an X Window System error.
This probably reflects a bug in the program.
The error was 'BadRequest (invalid request code or no such operation)'.
  (Details: serial 55 error_code 1 request_code 151 minor_code 19)
  (Note to programmers: normally, X errors are reported asynchronously;
   that is, you will receive the error a while after causing it.
   To debug your program, run it with the --sync command line
   option to change this behavior. You can then get a meaningful
   backtrace from your debugger if you break on the gdk_x_error() function.)
```

I searched for what this 'X Window System error' is but found no useful information. Can anyone help me with it?

Thanks.

---

### Post by deadflowr on 2015-04-13
Did you try the suggestion the message gave of running with the sync option?
```
pcsx --sync
```
hopefully it'll output something useful.

---

### Post by carega on 2015-04-14
I tried and got almost the same message with a slight difference:
```
carega@macross:~$ pcsx --sync
RGB mode found.  id: 18424752, depth: 24
The program 'pcsx' received an X Window System error.
This probably reflects a bug in the program.
The error was 'BadRequest (invalid request code or no such operation)'.
  (Details: serial 55 error_code 1 request_code 151 minor_code 19)
  (Note to programmers: normally, X errors are reported asynchronously;
   that is, you will receive the error a while after causing it.
   To debug your program, run it with the --sync command line
   option to change this behavior. You can then get a meaningful
   backtrace from your debugger if you break on the gdk_x_error() function.)
```

Does this help?

---

### Post by lbug7575 on 2015-04-19
[COLOR=#000000]Did you try the suggestion the message gave of running with the sync option?[/COLOR]

The error was 'BadRequest (invalid request code or no such operation)'.
  (Details: serial 55 error_code 1 request_code 151 minor_code 19)
  (Note to programmers: normally, X errors are reported asynchronously;
   that is, you will receive the error a while after causing it.
   To debug your program, run it with the --sync command line
   option to change this behavior. You can then get a meaningful...!!!!



__________________________________________________________________________
[http://www.solitaire-champ.com/klondike-solitaire.html](http://www.solitaire-champ.com/klondike-solitaire.html)
[www.solitaire-champ.com/download-free-solitaire.html](http://www.solitaire-champ.com/download-free-solitaire.html)

---

### Post by mrbigmouth502 on 2015-04-22
Try Mednafen. It's commandline based, but there are frontends available. I find it's a better emulator than PCSX-R, though it runs everything at native PSX resolution instead of upscaling things.

---

### Post by carega on 2015-04-22
> [COLOR=#000000]Did you try the suggestion the message gave of running with the sync option?[/COLOR]

Did you read what I wrote? I used the --sync option!!

@mrbigmouth502 I'll give it a go. After all I have nothing to lose.

---

### Post by carega on 2015-04-23
Mednafen doesn't emulate PSX. At least the version I found.

---

### Post by carega on 2015-05-16
hello, anyone?

---

