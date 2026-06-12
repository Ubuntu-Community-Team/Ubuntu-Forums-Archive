---
title: "Compilation Problems"
date: 2009-04-17
forum: General Help
---

### Post by jmg498 on 2009-04-17
I just recently reinstalled Ubuntu, this time on a logical partition instead of a VM, and am trying to install all of my old software.  One of the XMMS plugins I'm trying to build is Scizzor, for pitch control, but it errors out each time I try with nearly 600 lines of errors and warnings.  I copied just a few below.  I'm getting the feeling I'm missing something important (perhaps for gcc), but I did an apt-get update and upgrade and apparently everything is up to date.

Any suggestions would be greatly appreciated!  Thanks much!

```
scizzor.c:489: error: ‘TRUE’ undeclared (first use in this function)
scizzor.c: In function ‘scizzor_write_audio’:
scizzor.c:500: error: ‘struct <anonymous>’ has no member named ‘going’
scizzor.c:505: error: ‘struct <anonymous>’ has no member named ‘chnr’
scizzor.c:505: error: ‘struct <anonymous>’ has no member named ‘fmtsize’
scizzor.c:506: error: ‘struct <anonymous>’ has no member named ‘pitch’
scizzor.c:506: error: ‘struct <anonymous>’ has no member named ‘speed’
scizzor.c:507: error: ‘struct <anonymous>’ has no member named ‘volume_lock’
scizzor.c:508: error: ‘struct <anonymous>’ has no member named ‘handle’
scizzor.c:508: error: ‘struct <anonymous>’ has no member named ‘fmtsize’
scizzor.c:509: error: ‘struct <anonymous>’ has no member named ‘written’
scizzor.c:510: error: ‘struct <anonymous>’ has no member named ‘written’
scizzor.c:510: error: ‘struct <anonymous>’ has no member named ‘bpsec’
scizzor.c:511: error: ‘struct <anonymous>’ has no member named ‘written’
scizzor.c:511: error: ‘struct <anonymous>’ has no member named ‘bpsec’
scizzor.c:512: error: ‘struct <anonymous>’ has no member named ‘time_offs’
scizzor.c: In function ‘scizzor_close_audio’:
scizzor.c:519: error: ‘struct <anonymous>’ has no member named ‘going’
scizzor.c:519: error: ‘FALSE’ undeclared (first use in this function)
scizzor.c:520: error: ‘struct <anonymous>’ has no member named ‘written’
scizzor.c:521: error: ‘struct <anonymous>’ has no member named ‘time_offs’
scizzor.c:522: error: ‘struct <anonymous>’ has no member named ‘handle’
scizzor.c: In function ‘scizzor_flush’:
scizzor.c:527: error: ‘struct <anonymous>’ has no member named ‘written’
scizzor.c:528: error: ‘struct <anonymous>’ has no member named ‘time_offs’
scizzor.c: In function ‘scizzor_pause’:
scizzor.c:533: error: ‘struct <anonymous>’ has no member named ‘paused’
scizzor.c: In function ‘scizzor_buffer_free’:
scizzor.c:538: error: ‘struct <anonymous>’ has no member named ‘paused’
scizzor.c: In function ‘scizzor_buffer_playing’:
scizzor.c:547: error: ‘FALSE’ undeclared (first use in this function)
scizzor.c: In function ‘scizzor_output_time’:
scizzor.c:552: error: ‘struct <anonymous>’ has no member named ‘time_offs’
scizzor.c:552: error: ‘gint’ undeclared (first use in this function)
scizzor.c:552: error: ‘struct <anonymous>’ has no member named ‘written’
scizzor.c:552: error: ‘struct <anonymous>’ has no member named ‘bpsec’
scizzor.c: In function ‘scizzor_written_time’:
scizzor.c:557: error: ‘struct <anonymous>’ has no member named ‘time_offs’
scizzor.c:557: error: ‘gint’ undeclared (first use in this function)
scizzor.c:557: error: ‘struct <anonymous>’ has no member named ‘written’
scizzor.c:557: error: ‘struct <anonymous>’ has no member named ‘bpsec’
scizzor.c: At top level:
scizzor.c:560: error: expected ‘)’ before ‘*’ token
make: *** [xmms] Error 1

```

---

### Post by DustStuff on 2009-10-23
@ jmg498, I'm not sure if you (or others viewing this thread) are still working on this, but [this tutorial]("http://ubuntuforums.org/showthread.php?t=1282869") might help solve the problem.

---

