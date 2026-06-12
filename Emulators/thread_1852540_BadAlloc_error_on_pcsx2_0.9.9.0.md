---
title: "BadAlloc error on pcsx2 0.9.9.0"
date: 2011-09-30
forum: Emulators
---

### Post by BMBlues on 2011-09-30
Hi, some days ago i decided to start playing on pcsx2, since in Win 7 my frame rate was so slow ( 8 fps) i tried to install it on Ubuntu.

I checked the forum for the installation guide, no one of them really worked, finally after some hours i got pcsx2 0.9.9.0 from synaptic package manager. Everything went just fine, but suddenly the program crashes when i try to run some game (from a .mdf file).

The game have all his bios and plugins, i checked the website of pcsx2 if the emulator have some issues with the game (.Hack//G.U Rebirth) but it says is 100% playable.
I tried run it from terminal to have a log from the crash and this is what i got:
```
konkon@konkon-GeForce6100PM-M2:~$ pcsx2 &
[1] 19338
konkon@konkon-GeForce6100PM-M2:~$ Interface is initializing.  Entering Pcsx2App::OnInit!
Applying operating system default language...
Command line parsing...
Command line parsed!
ZZogl-PG: Calling GSinit.
ZZogl-PG: GSinit finished.
ZZogl-PG: Calling GSopen2.
ZZogl-PG: Capturing ZZOgl window.
ZZogl-PG:  Got Doublebuffered Visual!
The program 'pcsx2' received an X Window System error.
This probably reflects a bug in the program.
The error was 'BadAlloc (insufficient resources for operation)'.
  (Details: serial 29 error_code 11 request_code 136 minor_code 34)
  (Note to programmers: normally, X errors are reported asynchronously;
   that is, you will receive the error a while after causing it.
   To debug your program, run it with the --sync command line
   option to change this behavior. You can then get a meaningful
   backtrace from your debugger if you break on the gdk_x_error() function.)
```
I came to the conclusion that my pc doesn't have the enough resources to play things in emulators like this one (AMD sempron LE-1200, memory 873.6, GeForce 6150SE nForce 430), might be wrong?

---

