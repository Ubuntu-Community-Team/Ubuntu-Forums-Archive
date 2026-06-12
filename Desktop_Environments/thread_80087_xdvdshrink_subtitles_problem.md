---
title: "xdvdshrink subtitles problem"
date: 2005-10-21
forum: Desktop Environments
---

### Post by fotisman on 2005-10-21
I have xdvdshrink and it's great! BUt the problem is that it does not copy the subtitles to the new dvd. The option is disabled!

I have subtitleripper and gocr properly installed.

Any help?

---

### Post by fotisman on 2005-10-21
up

---

### Post by mcrosmar on 2005-10-21
[quote=fotisman]I have xdvdshrink and it's great! BUt the problem is that it does not copy the subtitles to the new dvd. The option is disabled!

I have subtitleripper and gocr properly installed.

Any help?[/quote] 
You must edit /usr/bin/xdvdshrink.pl to enable subtitles:

1)sudo gedit /usr/bin/xdvdshrink.pl
2) Go to line 969 and change 
[B]if ( qx/subtitle2pgm -h 2>&1/ !~ /-X/ ) {
[/B]to this
[B]if ( qx/subtitle2pgm -h 2>&1/ !~ // ) {
[/B]
I had the same problem and this was the only solution I found.

---

