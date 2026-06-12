---
title: "desmume"
date: 2008-02-10
forum: Gaming &amp; Leisure
---

### Post by rustysail on 2008-02-10
Hey
I have a nearly fresh copy of gutsy and I tried to install DeSmuME from the package manager and it won't open.  Here is the result of doing it from the terminal.

```
rusty@rusty-desktop:~$ desmume
Nbr of joysticks: 0

The program 'desmume' received an X Window System error.
This probably reflects a bug in the program.
The error was 'GLXBadContext'.
  (Details: serial 258 error_code 154 request_code 143 minor_code 5)
  (Note to programmers: normally, X errors are reported asynchronously;
   that is, you will receive the error a while after causing it.
   To debug your program, run it with the --sync command line
   option to change this behavior. You can then get a meaningful
   backtrace from your debugger if you break on the gdk_x_error() function.)
```

Thanks for the help

---

### Post by FrozenFox on 2008-02-10
Your best bet is to use No$GBA in Wine. It currently works wonderfully with wine 0.9.55, much better than desmume in general. 2.6a is especially awesome and much faster if you can "donate" the 2.50 to the author for the download link.

---

### Post by heatblazer on 2008-02-12
I tried it too. However neither of these emulators are working. I have no idea. I have the ROMS of the DS but the emus crush!

---

### Post by FrozenFox on 2008-02-12
Really? That's very strange. Did you decode them before you tried to run them in either emu? Kirby canvas curse, Diamond, and Pearl all work flawlessly for me in no$gba 2.6 in wine.

---

### Post by rustysail on 2008-02-12
no$gba appears to load the rom, but then it shows just what I think is japanese writing on the top screen.  Maybe I have a bad rom?

---

### Post by FrozenFox on 2008-02-12
It just might not be able to play your game. What are you trying to run? And for the record, what version of wine are you using?

---

### Post by rustysail on 2008-02-12
I was trying to run pokemon pearl

I got a new rom.  Same screen but this time in english.  It says
"The data could not be read.

Please turn off the power, then remove and reinsert the DS Game Card.

As for wine, I'm not sure.  it must be new cuz it is a brand new version of ubuntu.

---

### Post by FrozenFox on 2008-02-12
Games that crash or where "data cannot be read" typically have not been decrypted. Search for endcrypts advanced (im not sure if it works in wine) or get one that's patched already.

---

### Post by FrozenFox on 2008-02-12
Please see your private forum msgs, rusty. User CP --> private messages.

---

### Post by garukun on 2008-05-09
I'm running in Hardy, I am experiencing the exact same problem. Any experienced mind giving a "why" this is happening?

---

### Post by GumbyX on 2008-05-26
Got the same problem as you guys. I am doing NDS development and I can't get desmume to work at all. Same error as the first post on both 8.04 i386 and AMD64. :(

---

### Post by Zairinho12 on 2008-05-28
Fixing the "data could not be read" problem is usually very simple. What you need to do is Change the Save Type on your No$gba to Flash 512Kb. To do this, open your diamond/pearl rom in no$gba

then click on the options tab and emulation setup. in the dialog box labelled "nds cartridge backup media" click on FLASH 512 Kbytes.then click ok.

then click on file>reset cartridge. this usually should fix the data could not be read problem.

hope i've helped

---

### Post by Sockerdrickan on 2008-05-28
Also try compiling the new DeSmuME 0.8 to get other results [www.desmume.org](www.desmume.org)

---

### Post by FranMichaels on 2008-05-28
> **rustysail said:**
> Hey
I have a nearly fresh copy of gutsy and I tried to install DeSmuME from the package manager and it won't open.  Here is the result of doing it from the terminal.

```
rusty@rusty-desktop:~$ desmume
Nbr of joysticks: 0

The program 'desmume' received an X Window System error.
This probably reflects a bug in the program.
The error was 'GLXBadContext'.
  (Details: serial 258 error_code 154 request_code 143 minor_code 5)
  (Note to programmers: normally, X errors are reported asynchronously;
   that is, you will receive the error a while after causing it.
   To debug your program, run it with the --sync command line
   option to change this behavior. You can then get a meaningful
   backtrace from your debugger if you break on the gdk_x_error() function.)
```

Thanks for the help

Are you using compositing?

Try this, should work. :)

```
desmume --disable-3d
```

---

