---
title: "linux equivalent of ToneThis ????"
date: 2006-08-21
forum: Desktop Environments
---

### Post by lopzided on 2006-08-21
there is a program for windows called ToneThis. ( [http://www.tonethis.com/](http://www.tonethis.com/) ) ...my friend uses this software to send free ringtones to his cell phone.

i have tried getting this program to run under wine, but it won't work (something about .net)....

does anyone know an equivalent of this app for linux?  or maybe a way to make it work under wine?

thanks in advance!

---

### Post by lopzided on 2006-08-22
bump

---

### Post by MGStreak on 2007-08-30
Shameless re-bump

---

### Post by lopzided on 2007-09-01
glad to see someone else is interested in this!

after trying again, i realized i needed mono to run it.  after trying to run it again under mono, however, i get this : 

```
slop@slopbuntu:~/.wine/drive_c/Program Files/ToneThis 3.0$ mono ToneThis.exe

** (ToneThis.exe:17624): WARNING **: The following assembly referenced from /home/slop/.wine/drive_c/Program Files/ToneThis 3.0/ToneThis.exe could not be loaded:
     Assembly:   System.Windows.Forms    (assemblyref_index=1)
     Version:    1.0.5000.0
     Public Key: b77a5c561934e089
The assembly was not found in the Global Assembly Cache, a path listed in the MONO_PATH environment variable, or in the location of the executing assembly (/home/slop/.wine/drive_c/Program Files/ToneThis 3.0/).


** (ToneThis.exe:17624): WARNING **: Could not load file or assembly 'System.Windows.Forms, Version=1.0.5000.0, Culture=neutral, PublicKeyToken=b77a5c561934e089' or one of its dependencies.
The entry point method could not be loaded
slop@slopbuntu:~/.wine/drive_c/Program Files/ToneThis 3.0$
```

any ideas on this, anyone?

Thanks in advance!

---

### Post by Webby_s on 2007-09-17
No one must be having any luck in finding an alternative? Well that is a bummer, It would be awesome to be able to use ToneThis in Ubuntu.

:(

---

### Post by bjourne on 2007-09-17
I'm probably missing something, but why don't you just connect the phone to the computer via a usb cable and use it as a mass storage device? Then you just drag your ring tones to it.

---

### Post by lopzided on 2007-10-13
yeah, i WISH it was that easy lol

i can't remember why it doesn't work (i tried it a long time ago), but it doesn't.  i still have to use my doze laptop to run tonethis.  it sucks.

---

