---
title: "Acidrip doesn't show status/progress?"
date: 2006-07-01
forum: Desktop Environments
---

### Post by naked on 2006-07-01
I just have to guess how far along it is by looking at the file size of the avi file.

It shows the mini status mode, but nothing ever changes, and everything reads 0's.

L

---

### Post by dpaint4 on 2006-07-02
Yes. I can verify that this is true (the issue with no progress updates). Additionally, none of the audio choices properly sync with the output video except for AC3 passthrough mode. MP3 properly compresses, but for some reason is always ahead of or behind the video by a good portion.

I'd *like* to be using AAC audio for my rips, but that option is greyed out in Acidrip, even though FAAC and FAAD are installed on my system.

---

### Post by 315234 on 2007-12-29
This is due to an error in the regular expressions used to parse the mencoder output. To workaround, open the file /usr/share/perl5/AcidRip/acidrip.pm and change the line:
```

if (/^Pos:\s*(\d+).\ds\s+(\d+)f\s+\(\s*(\d+)%\)\s+(\d+fps)\sTrem:\s+(\d+min)\s+(\d+mb).+\[([\d:]+)\]/) {
```
to read:
```
if (/^Pos:\s*(\d+)[.]\ds\s+(\d+)f\s+\(\s*(\d+)%\)\s+(\d+[.]\d+fps)\sTrem:\s+(\d+min)\s+(\d+mb).+\[([\d:]+)\]/) {
```

This works for me. Mencoder version:
```
MEncoder dev-SVN-rUNKNOWN-4.1.2 (C) 2000-2006 MPlayer Team
CPU: Intel(R) Core(TM) Duo CPU      T2350  @ 1.86GHz (Family: 6, Model: 14, Stepping: 12)
CPUflags: Type: 6 MMX: 1 MMX2: 1 3DNow: 0 3DNow2: 0 SSE: 1 SSE2: 1
Compiled with runtime CPU detection.
```
If this does not fix the problem for you, have a look at your mencoder output and learn perl regular expressions (if you haven't already).

---

