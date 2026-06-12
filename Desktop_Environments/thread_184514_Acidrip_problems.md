---
title: "Acidrip problems"
date: 2006-05-30
forum: Desktop Environments
---

### Post by feight on 2006-05-30
This seems to be a fairly popular topic on the boards but the errors don't seem to match mine.

```
AcidRip message - Pushed events onto queue
AcidRip message - Playlist contains 4 item(s)
AcidRip message - Running unlink frameno.avi 2> /dev/null
AcidRip message - Removing frameno.avi if it exists
AcidRip message - Running mencoder dvd://6 -dvd-device /dev/dvd  -aid 129 -sid 0  -info srcform="DVD ripped by acidrip.sf.net" -oac mp3lame -lameopts abr:br=128  -ovc xvid -xvidencopts  :bitrate=641:pass=1 -vf pp=de,crop=0:0:0:0,scale=480:272    -o "/dev/null"
AcidRip message - Encoding film, 1st pass...
MEncoder 2:0.99+1.0pre7try2+cvs20060117-0ubuntu8 (C) 2000-2006 MPlayer Team
CPU: Advanced Micro Devices  (Family: 15, Stepping: 0)
CPUflags: Type: 15 MMX: 1 MMX2: 1 3DNow: 1 3DNow2: 1 SSE: 1 SSE2: 1
Compiled with runtime CPU detection.
91 audio & 204 video codecs
Option xvidencopts: Unknown suboption 

Exiting... (error parsing cmdline)
AcidRip message - Clearing 2 remaining playlist items
AcidRip message - Mencoder interrupted by user

```

It seems that it is having problems with xvidencopts because no option is chosen but there is a colon still in place for it that ends up right behind bitrate.

Any suggestions? I wouldn't bother if acidrip didn't appear to be 'exactly' what I need without spending several days I don't have learning other ripper/encoders in linux.

AviDemuxer2 appears fairly good but don't get me started on it's use of VobSub and I watch quite a bit of japanese anime.

---

### Post by feight on 2006-05-31
Okay, I found a thread that recognized the same problem as me, took me a while since you can't search for :bitrate it ends up looking for bitrate.

I'm now using the output created by Acidrip in command line. One small problem...

I'm ripping my personal copy of Escaflowne and trying to encode it in XVID but I have one question... why in some pages where they explain two-pass... do they export to /dev/null, I thought that destroyed everything you put into it?

---

### Post by hotani on 2006-07-16
and you fixed this... How?

I'm not finding any info on the problem, I could very likely be messing something up in AcidRip but this is the error I'm getting:

```

Option xvidencopts: Unknown suboption 

Exiting... (error parsing cmdline)

```

---

### Post by cosine7 on 2006-07-25
> **hotani said:**
> and you fixed this... How?

I'm not finding any info on the problem, I could very likely be messing something up in AcidRip but this is the error I'm getting:

```

Option xvidencopts: Unknown suboption 

Exiting... (error parsing cmdline)

```

This happend when i copied and pasted the acidrip in console and forgot to edit the :

---

### Post by hotani on 2006-07-25
I found a [helpful thread](http://www.ubuntuforums.org/showthread.php?t=15689) on this *bug* which provided a couple of workarounds.

---

### Post by oscar on 2006-08-10
I found a solution which is to input the video options yourself. In the video tab manually enter the options that you want. I found some examples on the mplayer site:
[http://www.mplayerhq.hu/DOCS/HTML/en/menc-feat-xvid.html#menc-feat-xvid-example-settings](http://www.mplayerhq.hu/DOCS/HTML/en/menc-feat-xvid.html#menc-feat-xvid-example-settings)
I have only tried the very high quality line but I imagine the others work too.

---

### Post by crack on 2006-12-01
cosine7 said what to do, but in a strange way he did that :)


copy the 'mencoder....' from log of the acidrip and remove the ':' infront the bitrate it should do the trick, at least i'm ripping moview rite now, hope it'll turn out ok :)

---

### Post by cosine7 on 2006-12-01
> **crack said:**
> cosine7 said what to do, but in a strange way he did that :)

Note to self. Need better ppl skills :-D

---

