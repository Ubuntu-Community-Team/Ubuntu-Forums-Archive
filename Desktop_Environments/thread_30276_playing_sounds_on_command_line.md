---
title: "playing sounds on command line"
date: 2005-04-28
forum: Desktop Environments
---

### Post by daryl314 on 2005-04-28
does anyone know of a command in kubuntu that will play sounds (specifically wav files) from the command line?  i used to use the 'play' command in libranet.  my arts server stopped working on me, and i'm trying to find a workaround using oss or something.

---

### Post by RaverDK on 2005-04-28
[QUOTE=daryl314]does anyone know of a command in kubuntu that will play sounds (specifically wav files) from the command line?  i used to use the 'play' command in libranet.  my arts server stopped working on me, and i'm trying to find a workaround using oss or something.[/QUOTE]
 Arhm thinking about mpg123 - it plays also MP3 files just from the commandpromt

---

### Post by philipacamaniac on 2005-04-28
Try alsaplayer. You can also configure Kaffeine and amaroK to use the xine engine, which I think bypasses arts.

---

### Post by daryl314 on 2005-04-29
thanks for the advice.  i just wanted to post what i found out after poking around for a while in case it helps someone else.  installing the SoX package sets up the 'play' script which does what i am looking for.

---

### Post by heimo on 2005-04-29
```
cat file.wav > /dev/dsp
```
:roll:

---

