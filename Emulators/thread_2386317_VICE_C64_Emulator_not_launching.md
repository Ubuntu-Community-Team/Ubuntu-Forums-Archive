---
title: "VICE C64 Emulator not launching"
date: 2018-03-03
forum: Emulators
---

### Post by galacticstone on 2018-03-03
Hi Folks,

I just tried downloading the VICE Commodore 64 emulator from the USC. It downloaded fine (SNAP) and it now appears in my main menu, but it cannot be launched. I tried rebooting and still nothing happens - go GUI appears, nothing. Am I missing something obvious or is there an issue?

Thanks!

MikeG

---

### Post by kostkon on 2018-03-04
It isn't working here either, I get this in the terminal:
```
>>~> vice-jz.x64
Detecting ISA HardSID boards.
Could not open '/dev/port'.
Bad system call (core dumped)
```

Feel free to file a bug report on [its github page]("https://github.com/jacobzimmermann/vice-jz-snap"), hopefully it will be seen.

The version of vice in the 16.04 repos is really old, so a snap version that actually works would obviously be preferable.

---

### Post by galacticstone on 2018-03-04
Thanks, I thought it might just be me because I am running Gnome-Flashback as my desktop. I'm not a member of Github, so it won't let me post a bug report.

---

### Post by kostkon on 2018-03-06
> **galacticstone said:**
> I'm not a member of Github, so it won't let me post a bug report.
I guess one of us could try [contacting the packager directly]("https://uappexplorer.com/snap/ubuntu/vice-jz"), you wanna?

---

### Post by galacticstone on 2018-03-09
I had thought about that, but I wasn't sure if that was poor protocol or not - pestering a developer via email because I can't play games.  LOL.

---

