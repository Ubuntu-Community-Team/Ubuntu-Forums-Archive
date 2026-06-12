---
title: "libdvdcss problem"
date: 2005-03-15
forum: Desktop Environments
---

### Post by cory-79 on 2005-03-15
Hi, I'm new in this forum.
I post because I've a problem with dvd
I've installed totem anda libdvdcss, but totem (and vlc) doesn't seem to find libdvdcss, when launch totem and try to play a dvd i get this error

```
The source seems encrypted, and can't be read. Are you trying to play an encrypted DVD without libdvdcss?
``` 

and when I try to open a dvd with vlc I get:

```
libdvdread: Attempting to retrieve all CSS keys
libdvdread: This can take a _long_ time, please be patient  
libdvdread: Get key for /VIDEO_TS/VTS_01_1.VOB at 0x00000150
libdvdread: Error cracking CSS key for /VIDEO_TS/VTS_01_1.VOB (0x00000150)!! 
libdvdread: Elapsed time 4 libdvdread: Get key for /VIDEO_TS/VTS_02_1.VOB at 0x000256a6 
libdvdread: Error cracking CSS key for /VIDEO_TS/VTS_02_1.VOB (0x000256a6)!! 
libdvdread: Elapsed time 0 libdvdread: Found 2 VTS's 
libdvdread: Elapsed time 4 
``` 

Thanks in advance for any help

---

### Post by wbeck85 on 2005-03-15
Did you JUST install libDVDcss? Actually, I had the same problem today. I inserted a DVD, got the error in totem-xine, went online, found out about the lib and installed it, tried totem-xine again and got the same error. I was confused for a long while -Until i ejected the disc and reinserted it. Then it worked fine. Weird.
Oh, if it is really choppy, there's a command that has something to do with setting something DMA to 1, but you can search for that yourself. Goodluck.

---

### Post by cory-79 on 2005-03-21
I've got the problem

in file ~/.gnome/totem_config I have this line quoted

```

# CSS decryption method 
# { key  disc  title }, default: 0 
#media.dvd.css_decryption_method:key
``` 

simply unquote the last line and get the css work

```

# CSS decryption method 
# { key  disc  title }, default: 0
media.dvd.css_decryption_method:key
```

---

