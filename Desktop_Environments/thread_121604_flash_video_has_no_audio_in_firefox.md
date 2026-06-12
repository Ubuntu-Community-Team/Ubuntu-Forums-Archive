---
title: "flash video has no audio in firefox"
date: 2006-01-25
forum: Desktop Environments
---

### Post by rossellamj on 2006-01-25
Hello, can anybody help with this: I've tried everything to make the audio work when I watch a flash video in firefox. I've got all the necessary plugins from what I can tell but still no audio, I can see the video fine though. If somebody can give me a tip I would really appreciate it. Thanks in advance.

---

### Post by mustang on 2006-01-25
See 
[https://wiki.ubuntu.com/RestrictedFormats#head-832969c4301548599ecbe6393e2682a4e343af67](https://wiki.ubuntu.com/RestrictedFormats#head-832969c4301548599ecbe6393e2682a4e343af67)

Play around with the sound environment. E.g. try:

FIREFOX_DSP="none"
FIREFOX_DSP="ESD"
FIREFOX_DSP="ALSA"

---

