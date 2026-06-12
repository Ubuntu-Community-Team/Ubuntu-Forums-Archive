---
title: "weird totem problems (uncommon)"
date: 2005-05-14
forum: Desktop Environments
---

### Post by zbrox on 2005-05-14
i know there are a lot of totem questions but this one is not one of them. i searched many forums and still can't figure this out. i install totem with xine as a backend. i install the newest w32codecs package and still there are these avis and one mpg that i just can't open with totem. i afterwards install things like xvidcore and some divx packages but still nothing. the totem says it can't find a suitable module for this video file and nothing. no thumbnailing for it of course, cause it won't play it.
here's what xine gave me as a error message:

> 'video_out: throwing away image with pts 131978 because it's too old (diff : 11864).'
 'video_out: throwing away image with pts 128978 because it's too old (diff : 14864).'
 'video_out: throwing away image with pts 125978 because it's too old (diff : 17864).'
 'video_out: throwing away image with pts 122978 because it's too old (diff : 20864).'
 'video_out: throwing away image with pts 95978 because it's too old (diff : 4536).'
 'video_out: throwing away image with pts 92978 because it's too old (diff : 7536).'
 'xine: found demuxer plugin: Elementary MPEG stream demux plugin'
 'xine: found input plugin  : file input plugin'
 'xine: couldn't find demux for >Video.avi<'
 'xine: found input plugin  : file input plugin'


this is it. i hope some of you can help me, cause i'm really stuck! thank you in advance!

---

### Post by ludi on 2005-05-14
Have you installed the avifile-win32-plugin or the libavifile-07c102 ?
I just have the avifileplguin and I didn't have any troubles so far.
Whatever, I think that the plugin should work, if don't, try the libavi or recompile your xine to support whatever you want.

---

### Post by jnow on 2006-05-13
this my problem:
video_out: throwing away image with pts 2565881 because it's too old (diff : 42061).
video_out: throwing away image with pts -45364879 because it's too old (diff : 47975264).
video_out: throwing away image with pts 2562101 because it's too old (diff : 75218).
video_out: throwing away image with pts 2565881 because it's too old (diff : 99470).
video_out: throwing away image with pts 2569571 because it's too old (diff : 124397).
video_out: throwing away image with pts 2573351 because it's too old (diff : 150668).
video_out: throwing away image with pts 2577131 because it's too old (diff : 177762).
video_out: throwing away image with pts 2580821 because it's too old (diff : 201985).

(gnome_segv2:4252): Pango-WARNING **: Error loading GPOS table 40

and i playing a rmvb file

my video card is ATI M6LY

---

