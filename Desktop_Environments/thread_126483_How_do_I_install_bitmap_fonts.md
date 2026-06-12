---
title: "How do I install bitmap fonts?"
date: 2006-02-06
forum: Desktop Environments
---

### Post by hornett on 2006-02-06
I have a nice bitmap font (in .pcf format) which I would like to install (get it [here]("http://www.tobias-jung.de/seekingprofont/"))

Can anybody give me a clue where to begin?

I've tried putting the files into ~/.fonts but they wont appear in my fonts lists in applications...

```
retro@d600:~/.fonts$ fc-cache -f -v
fc-cache: "/usr/share/fonts": skipping, no write access
fc-cache: "/usr/share/X11/fonts": skipping, no write access
fc-cache: "/usr/local/share/fonts": skipping, no write access
fc-cache: "/home/retro/.fonts": caching, 31 fonts, 0 dirs

```

```
retro@d600:~/.fonts$ pwd
/home/retro/.fonts
retro@d600:~/.fonts$ ls -l | grep .pcf
-rw-r--r--  1 retro retro  18080 2006-02-06 21:26 ProFont_r400-10.pcf
-rw-r--r--  1 retro retro  19104 2006-02-06 21:26 ProFont_r400-11.pcf
-rw-r--r--  1 retro retro  20128 2006-02-06 21:26 ProFont_r400-12.pcf
-rw-r--r--  1 retro retro  23200 2006-02-06 21:26 ProFont_r400-15.pcf
-rw-r--r--  1 retro retro  25252 2006-02-06 21:26 ProFont_r400-17.pcf
-rw-r--r--  1 retro retro  30372 2006-02-06 21:26 ProFont_r400-22.pcf
-rw-r--r--  1 retro retro  37540 2006-02-06 21:26 ProFont_r400-29.pcf

```

Cheers! :mrgreen:

---

