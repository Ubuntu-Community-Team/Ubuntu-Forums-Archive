---
title: "How do I record video off epsxe?"
date: 2007-08-27
forum: Gaming &amp; Leisure
---

### Post by darkadvice on 2007-08-27
I'm trying to capture footage of Final Fantasy VIII for a Video Game Rant, but I just can't seem to find a good way to do it. I've googled alot and all  the advice for direct epsxe video capturing doesn't have a linux version (P.E.Op.S softgpu with record feature) and trying to use basic Record desktops, Recordmy desktop, Istanbul and even VLC screen, just makes the game chuggy or frame rates all over the place. 

Has anyone figured a way to get a good constant video record of epsxe on linux?

---

### Post by acoustibop on 2007-08-27
Any desktop recorder wil slow your system down appreciably, darkadvice.  I think there are external recorders available, but I don't know much about them.

The best in-system one I've come across (and least resource using) is gvidcap - if you google you should be able to find a deb file.  There isn't as recent a version available as for its companion, xvidcap, but xvidcap won't record emulators (AIR it won't record 3D).

Another approach is to use an emulator that uses less resources - try [pSX Emulator]("http://psxemulator.gazaxian.com/").  IMHO it's a better emulator anyway; it's still in active development.  ePSXe's last update was 4 years ago.

---

### Post by migatxu on 2007-08-27
Well... I've recorded Pocket Fighter on epsxe with recordMyDesktop and compiz running on the machine, without problems, with a C2D E6300 Nvidia  7300GT 256MB and 1Gb of ram. Look out the opcions in recordMyDesktop, there is something for 3D Maybe... I don't know... Get lucky!

---

### Post by darkadvice on 2007-08-27
> **acoustibop said:**
> Any desktop recorder wil slow your system down appreciably, darkadvice.  I think there are external recorders available, but I don't know much about them.

The best in-system one I've come across (and least resource using) is gvidcap - if you google you should be able to find a deb file.  There isn't as recent a version available as for its companion, xvidcap, but xvidcap won't record emulators (AIR it won't record 3D).

Another approach is to use an emulator that uses less resources - try [pSX Emulator]("http://psxemulator.gazaxian.com/").  IMHO it's a better emulator anyway; it's still in active development.  ePSXe's last update was 4 years ago.

Well i couldn't find a gvidcap .deb anywhere, so i tried out xvidcap  and it doesn't cause any lag while emulator is running in windowed mode.... butt it won't record any sound. Can anybody tell me  what i have to do to record sound?

---

### Post by AFOH on 2010-08-02
I was looking for a way to record an epsxe session, too, and then came across this thread. I tried various different programs before following migatxu's suggestion. I quote:

> Well... I've recorded Pocket Fighter on epsxe with recordMyDesktop [without problems]. [...] Look out the [options] in recordMyDesktop, there is something for 3D Maybe... I don't know... Get lucky!

After examining a manual for said program, I encountered one option that will enable recordmydesktop to encode video from any window containing 3D [--full-shots]. (If such option is not specified prior to the recording, any 3D window will not be captured properly, or captured at all.) (Source: [http://recordmydesktop.sourceforge.net/manpage.php](http://recordmydesktop.sourceforge.net/manpage.php))

This option is enabled as an extra parameter after issuing the main command (which, in this case, is "recordmydesktop") in a command line, as follows:

```
recordmydesktop --full-shots
```

On inputting this command, recordmydesktop should start capturing your whole desktop session.* To stop the capture, hit Ctrl-C at any time, and wait until the program has finished encoding your session (a percentual indicator will keep you informed of the advance). When the encoding process is finished, the program will shut itself down. By default, the final product of this encoding will be a video file named "out.ogg" which will be located in your user folder, although, as the man page linked above shows, these are modifiable variables.

*Some people experience a problem with their sound devices while using recordmydesktop, which forces them to record using the "--no-sound" option (as is my case right now), although there are various fixes available in other threads for this situation. (I haven't begun searching for a fix that works, yet, but from what I've seen so far, this calamity is easily solved.)

Good luck.

---

