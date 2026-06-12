---
title: "Can't watch a DVD in Movie player, Mplayer or VLC"
date: 2009-05-29
forum: General Help
---

### Post by blue carrot on 2009-05-29
Hi guys,
Im trying to watch a DVD on my computer for the first time, and it doesn't work...the DVD is a legit copy of BBC 'planet earth'. 

When I try to open it with MPlayer, it says 'seek failed'.

When I try to open it with Movie Player, it plays the first 45 second intro bit of the DVD and then it says "an error occured: could not read from resource"

VLC doesn't work either.

Any help here?

---

### Post by Primefalcon on 2009-05-29
install medibuntu repository, [https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)

and install w32codecs or w64codecs if your using 64 bit and the libdvdcss2 packages

---

### Post by fillintheblanks on 2009-05-29
[http://ubuntuforums.org/showthread.php?t=766683](http://ubuntuforums.org/showthread.php?t=766683)

check DVD section

---

### Post by Soul-Sing on 2009-05-29
> **Primefalcon said:**
> install medibuntu repository, [https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)

and install w32codecs or w64codecs if your using 64 bit and the libdvdcss2 packages

w32/64codecs are of very little use playing dvd's.
( In fact i don't use them at all)
Gstreamer package does the job, with libdvdcss2.

: [http://ubuntuforums.org/showthread.php?t=766683](http://ubuntuforums.org/showthread.php?t=766683)
very useful indeed.

---

### Post by blue carrot on 2009-05-29
I tried installing the reccomended things and it turns out I already had them installed. So I still can't watch DVD's. Any more suggestions?

---

### Post by mhgsys on 2009-05-29
Try this;

```

sudo apt-get install libdvdread4

```

```

sudo /usr/share/doc/libdvdread4/install-css.sh

```

---

### Post by darthmob on 2009-05-29
> **mhgsys said:**
> Try this;
```

sudo apt-get install libdvdread4

```
```

sudo /usr/share/doc/libdvdread4/install-css.sh

```

I second that. more info here: [https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs](https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs)

---

### Post by blue carrot on 2009-05-29
Thanks, that fixed it.

---

### Post by Insoc on 2009-05-29
I'm having the same problem, installed VLC through synaptic along with everything else that was listed to install and still cannot play a DVD?

I using 9.04, though I don't see that listed on VLC only 8.10.

Anyone?

---

### Post by Teabicky on 2010-06-27
I have done all of the above and still nothing..... grrrrr. I am using an Fujitsu Lifebook N series.

---

