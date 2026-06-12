---
title: "UT2004 Karmic"
date: 2009-10-29
forum: Gaming &amp; Leisure
---

### Post by Drezliok on 2009-10-29
I upgraded an found my UT2004 doesn't work. I had to install libstdc++.so.5 from 9.04. After that hurdle I got his error.

```
drezliok@drezliok-desktop:~$ ut2004
open /dev/[sound/]dsp: Device or resource busy
X Error of failed request:  BadValue (integer parameter out of range for operation)
  Major opcode of failed request:  130 (XFree86-VidModeExtension)
  Minor opcode of failed request:  10 (XF86VidModeSwitchToMode)
  Value in failed request:  0x13c
  Serial number of failed request:  167
  Current serial number in output stream:  168

```
Game crashes. looks like sound and video effected.
I have no clue as to what to do now.

---

### Post by Drezliok on 2009-10-30
I tried to force it into safe mode with ```
ut2004 -safe
``` Same Error.

---

### Post by Brebs on 2009-10-30
Hopefully, ~/.ut2004/System/UT2004.log will provide better info about the crash.

---

### Post by Drezliok on 2009-10-31
> **Brebs said:**
> Hopefully, ~/.ut2004/System/UT2004.log will provide better info about the crash.

There is no log file. So no new progress.

---

### Post by Drezliok on 2009-10-31
FIXED!!!

The log file was in my settings folder. I was thinking like a windows user and forgot all the settings and such in my home directory.

I backed up my ut2004.ini and tried running the game knowing it would regenerate the file.

It generated the file and ran the game.

---

### Post by Brebs on 2009-11-01
> **Drezliok said:**
> my settings folder
Exactly what directory are you referring to?

---

### Post by Drezliok on 2009-11-01
> **Brebs said:**
> Exactly what directory are you referring to?

The one in your post.

I was thinking like a windows user and thought the configuration files would be with the game, rather than in my home folder. I spent a few days searching in my limited spare time to find the settings in the system folder where the game was installed. then I remembered that it wouldn't be there.

The settings called for a greater resolution than I had set up in my x11, so it would crash.

---

