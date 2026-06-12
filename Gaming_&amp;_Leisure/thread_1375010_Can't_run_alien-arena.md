---
title: "Can't run alien-arena"
date: 2010-01-07
forum: Gaming &amp; Leisure
---

### Post by riminicat on 2010-01-07
I get this error when I run from terminal:

```
using /home/william/.alien-arena/data1/ for writing
using /home/william/.alien-arena/arena/ for writing
execing default.cfg
bind <key> [command] : attach a command to a key
Unknown command "wave 4"
couldn't exec config.cfg
Console initialized.

------- sound initialization -------
bt_audio_service_open: connect() failed: Connection refused (111)
bt_audio_service_open: connect() failed: Connection refused (111)
bt_audio_service_open: connect() failed: Connection refused (111)
bt_audio_service_open: connect() failed: Connection refused (111)
AL lib: oss.c:179: Could not open /dev/dsp: Device or resource busy

```

Do you guys know how to fix this?  I don't know enough about the system to go modifying things on my own yet(-:

---

### Post by Perfect Storm on 2010-01-07
Try this fix (the audio): [http://ubuntuforums.org/showpost.php?p=8574436&postcount=23](http://ubuntuforums.org/showpost.php?p=8574436&postcount=23)

---

### Post by riminicat on 2010-01-07
still getting the same error

---

### Post by Jestersage on 2010-01-08
I used the method described here:: (Running x64 9.10):

[http://www.webupd8.org/2009/12/alien-arena-733-released-with-lots-of.html](http://www.webupd8.org/2009/12/alien-arena-733-released-with-lots-of.html)

> 
This is because of some Pulse Audio issues with OpenAL. But I've found a fix. If you also experience this error, edit the */etc/openal/alsoft.conf* file. To do this, open terminal and type
```

gksu gedit /etc/openal/alsoft.conf
```
Now search for the line that looks like this (it's on line 70 on my Ubuntu Karmic PC):
```
#drivers = alsa,oss,solaris,dsound,winmm,port,pulse,wave

```
and uncomment it (remove the "#" at the beginning of the line) and also, remove "pulse" from this list. Basically, after the change, this line should look like this:
```
drivers = alsa,oss,solaris,dsound,winmm,port,wave

```
And save the file, then run crx again.


---

### Post by riminicat on 2010-01-08
Thank you both! I had edited that file before, but forgot to uncomment it! It works now.

---

### Post by verlyn13 on 2010-01-16
Easy fix, thanks!

---

