---
title: "kino crashes when exporting :/"
date: 2006-07-06
forum: Desktop Environments
---

### Post by th0mas on 2006-07-06
i've been using kino since some days but today, it was the first time i tried to export.
and i'm very disappointed cause Kino always crashes...
I tried with different .avis, storyboard...
I also tried with a very short mpeg 2 .avi (6Mo / 4 sec).
Here is some crash example.

```
>> Starting Export
>> Starting ExportAVI
>> Export::activate()
>>> Trying export-test001.avi

Kino experienced a segmentation fault.
Dumping stack from the offending thread

Obtained 10 stack frames.
kino(__gxx_personality_v0+0x322) [0x8071b42]
[0xffffe420]
kino(_ZN8AVI2File10WriteFrameERK5Frame+0x26f) [0x809bf4d]
kino(_ZN10AVIHandler5WriteERK5Frame+0x1f) [0x8093f0b]
kino(_ZN11FileHandler10WriteFrameERK5Frame+0x8b) [0x8095335]
kino(_ZN9ExportAVI8doExportEP8PlayListiiib+0x609) [0x80bf0b1]
kino(_ZN6Export11startExportEb+0x282) [0x80bcdf0]
kino(_ZN10PageExport11startExportEv+0x3c) [0x80b982c]
kino(startExport+0x1b) [0x80d5f4d]
/usr/lib/libgobject-2.0.so.0(g_cclosure_marshal_VOID__VOID+0x43) [0xb775c423]

Done dumping - exiting.

```

help ! :-|

---

### Post by th0mas on 2006-07-06
btw, here are some hw details from my laptop :
- Ati Radeon Mobility 9200
- Pentium 4, 2.8GHz
- RAM 512 Mo (DDR-SDRAM PC2100 266 MHz)

I use Kino 0.80-1ubuntu7 (Dapper) with an updated dapper
Seems this version is not very stable...

thanks in advance if you can help ! :)

---

