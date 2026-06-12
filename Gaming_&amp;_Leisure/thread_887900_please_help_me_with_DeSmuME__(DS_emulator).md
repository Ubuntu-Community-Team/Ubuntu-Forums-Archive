---
title: "please help me with DeSmuME  (DS emulator)"
date: 2008-08-12
forum: Gaming &amp; Leisure
---

### Post by tjwoosta on 2008-08-12
i installed DeSmuME nintendo ds emulator  (from Add/Remove programs)

but it doesnt work

i have ubuntu hardy 64bit 

this is the error i get when i try to run the program

```

tj@tj-laptop:~$ desmume
Nbr of joysticks: 1

Joystick 0 Jess Tech GGE909 PC Recoil Pad
Axes: 6
Buttons: 12
Trackballs: 0
Hats: 0

The program 'desmume' received an X Window System error.
This probably reflects a bug in the program.
The error was 'GLXBadContext'.
  (Details: serial 298 error_code 154 request_code 143 minor_code 5)
  (Note to programmers: normally, X errors are reported asynchronously;
   that is, you will receive the error a while after causing it.
   To debug your program, run it with the --sync command line
   option to change this behavior. You can then get a meaningful
   backtrace from your debugger if you break on the gdk_x_error() function.)
tj@tj-laptop:~$ 


```

also i get the same exact error when i try to run desmume-glade 

and if i try to run desmume --sync it still gives the same exact error

---

### Post by FranMichaels on 2008-08-12
Run it as
```
desmume --disable-3d
```

---

### Post by tjwoosta on 2008-08-12
thank you, it worked

---

### Post by RealG187 on 2008-08-25
Just my luck this topic is only a week old.

I get that error and when I use no3d it works, kinda.

The emu opens and I pick the rom but all I get is white screen(s).

---

### Post by tjwoosta on 2008-08-28
i get the white screens with certain roms like zelda an new super mario, but it works fine for me with alot of other roms

---

### Post by Grishka on 2008-08-28
DeSmuME's performance is still sub-optimal, at best. I'd recommend No$gba ([http://nocash.emubase.de/gba.htm](http://nocash.emubase.de/gba.htm)) as the best working nds emulator to date. it's windows-only, but it works very well under Wine. if you'd prefer a Linux emulator, try iDeaS ([http://www.ideasemu.org/](http://www.ideasemu.org/)), it generally works much better than DeSmuME, albeit it's sound plugin is currently broken, so you'd have to play with the sound turned off, or cope with it's terribly garbled, choppy audio.

---

### Post by RealG187 on 2008-08-28
> **tjwoosta said:**
> i get the white screens with certain roms like zelda an new super mario, but it works fine for me with alot of other roms

Well I know you had to configure the save type, but thre is no where to do that here...

---

### Post by Amurko on 2009-10-24
> **tjwoosta said:**
> i get the white screens with certain roms like zelda an new super mario, but it works fine for me with alot of other roms

Go to their website (desmume.org) and download the latest version (0.9.4) in source.  Compile and install (read their instructions; there's also a file "missing" that's misnamed: po/Makefile.in)

Anyways, I now have Dragon Quest IV working where version 0.9.1 in the repositories gives me a blank screen (and No$GBA 2.6 in Wine or Virtualbox fails to save and load states properly.)

---

