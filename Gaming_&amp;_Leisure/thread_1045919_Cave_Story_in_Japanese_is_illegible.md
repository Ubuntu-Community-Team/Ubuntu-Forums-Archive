---
title: "Cave Story in Japanese is illegible"
date: 2009-01-20
forum: Gaming &amp; Leisure
---

### Post by japtar10101 on 2009-01-20
A strange question.  I already played the majority of Cave Story in english, and I wanted to re-play it in Japanese using the original Windows zip file with Ubuntu and Wine.  Lo an behold the completely unreadable text:
[IMG]http://i9.photobucket.com/albums/a87/japtar10101/Scrap/Screenshot-1-2.png[/IMG]

Is there a way to fix this?  The README file is only legible when I open it with open office, using either "Japanese (Apple Macintosh)/(Windows-932)/(Shift-JIS)", so I'm guessing I have to somehow run Wine supporting these character formats.

---

### Post by Catboy~ on 2009-01-21
Have you tried this already?
[http://ubuntuforums.org/showthread.php?t=383628](http://ubuntuforums.org/showthread.php?t=383628)

Hope that helps ;)

---

### Post by japtar10101 on 2009-01-23
> **Catboy~ said:**
> Have you tried this already?
[http://ubuntuforums.org/showthread.php?t=383628](http://ubuntuforums.org/showthread.php?t=383628)

Hope that helps ;)

Almost.  The dashes are screwed up.

---

### Post by japtar10101 on 2009-01-23
[IMG]http://i9.photobucket.com/albums/a87/japtar10101/Scrap/Screenshot-2-1.png[/IMG]

---

### Post by japtar10101 on 2009-01-24
Am I missing some Japanese fonts for dashes or something (thus the boxes)?  Or does Wineloc not support japanese dashes?

---

### Post by japtar10101 on 2009-01-24
Strange, but solved.  This command worked awesome:
```

LANG=ja_JP.UTF-8 wine application.exe

```

---

