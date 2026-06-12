---
title: "Is there anyway to save mms streams to hardrive?"
date: 2006-06-21
forum: Desktop Environments
---

### Post by Kouya on 2006-06-21
I have been trying all methods.Mplayer did not work. 

I can stream mms files and realmedia player files fine in gxine. But I want to be able to download and keep them in mp3 or .wav or some more normal format. Is that possible?

I found [http://www.geocities.com/majormms/](http://www.geocities.com/majormms/) and [http://mms-qt.sourceforge.net/](http://mms-qt.sourceforge.net/) where they give a method and client to compile. I've tried but I can't seem to compile them at all.

Is there any other way, anyone out there knows?

---

### Post by michelinux on 2006-06-21
I usually do:

```
mplayer -dumpstream mms://www.mysite.com/video.wmv -dumpfile saved-video.wmv
```

This works for me, using the mplayer in Ubuntu (Dapper) repositories.
Bye
Michele

---

### Post by Kouya on 2006-06-22
sorry to sound like a noob but I can't find the "mms://www.mysite.com/video.wmv" part....how do you get it?

---

### Post by Kouya on 2006-06-22
i tried look for a mms stream but all i got was this ...

mms://gwms32.streamos.com/32/78/57/78572fd855d2cb26d3481f0dad5c69aa-4494d6a8.asf?ts=1150964300&ttl=300&cs=9FB207973D4B288DD8923A463742A00B065BD5

if it does not end with .wmv, is it still possible to do what u said above?

---

### Post by michelinux on 2006-06-22
```
mplayer -dumpstream mms://gwms32.streamos.com/32/78/57/78572fd855d2cb26d3481f0dad5c69aa-4494d6a8.asf -dumpfile save.asf
```

All the rest are parameters for the mms/http server.

---

### Post by Kouya on 2006-06-22
```
bea@ubuntu:~$ mplayer -dumpstream mms://gwms32.streamos.com/32/78/57/78572fd855d2cb26d3481f0dad5c69aa-4494d6a8.asf -dumpfile save.asf
MPlayer 2:0.99+1.0pre7try2+cvs20060117-0ubuntu8 (C) 2000-2006 MPlayer Team
CPU: Advanced Micro Devices Athlon 64 Newcastle,Winchester,San Diego,Venice; Sempron Palermo (Family: 15, Stepping: 0)
CPUflags:  MMX: 1 MMX2: 1 3DNow: 1 3DNow2: 1 SSE: 1 SSE2: 1
Compiled with runtime CPU detection.


91 audio & 204 video codecs
Linux RTC init error in ioctl (rtc_irqp_set 1024): Permission denied
Try adding "echo 1024 > /proc/sys/dev/rtc/max-user-freq" to your system startup scripts.
Opening joystick device /dev/input/js0
Can't open joystick device /dev/input/js0: No such file or directory
Can't init input joystick
Setting up LIRC support...
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support.
You will not be able to use your remote control.
Playing mms://gwms32.streamos.com/32/78/57/78572fd855d2cb26d3481f0dad5c69aa-4494d6a8.asf.
STREAM_ASF, URL: mms://gwms32.streamos.com/32/78/57/78572fd855d2cb26d3481f0dad5c69aa-4494d6a8.asf
Resolving gwms32.streamos.com for AF_INET6...
Couldn't resolve name for AF_INET6: gwms32.streamos.com
Resolving gwms32.streamos.com for AF_INET...
Connecting to server gwms32.streamos.com[69.27.174.125]: 1755...
Connected
read error:: Operation now in progress
pre-header read failed
Resolving gwms32.streamos.com for AF_INET6...
Couldn't resolve name for AF_INET6: gwms32.streamos.com
Resolving gwms32.streamos.com for AF_INET...
Connecting to server gwms32.streamos.com[69.27.174.125]: 80...
Resolving gwms32.streamos.com for AF_INET6...
Couldn't resolve name for AF_INET6: gwms32.streamos.com
Resolving gwms32.streamos.com for AF_INET...
Connecting to server gwms32.streamos.com[69.27.160.125]: 80...
Cache size set to 64 KBytes
Stream not seekable!
Core dumped ;)

Exiting... (End of file)
```

it still does not work for me....the output has the last line of stream not seekable...what does that mean?

what is wrong? sorry for all the bother...

---

### Post by Pirate on 2006-12-12
you can save them also with vlc player

---

### Post by dailer on 2006-12-13
just install mimms
```
sudo apt-get install mimms
```

---

### Post by freeflyer57 on 2007-09-15
The problem is not the "stream not seekable" part. That is part of the stream setting. It looks like from your output that it can't find the source. Hope that helped.

---

### Post by aspora.isernia on 2008-01-27
> **dailer said:**
> just install mimms
```
sudo apt-get install mimms
```

Wow... This is EXACTLY what the thread requested.
Nice shot!!

a.i :)

---

### Post by zirtik on 2008-02-09
Works great! Thank you...

---

### Post by henriquemaia on 2008-05-15
> **michelinux said:**
> I usually do:

```
mplayer -dumpstream mms://www.mysite.com/video.wmv -dumpfile saved-video.wmv
```This works for me, using the mplayer in Ubuntu (Dapper) repositories.
Bye
Michele

Great tip! Thanks a lot Michele.

---

