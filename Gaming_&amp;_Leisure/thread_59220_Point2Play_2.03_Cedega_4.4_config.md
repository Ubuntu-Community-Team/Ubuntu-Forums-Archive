---
title: "Point2Play 2.03/ Cedega 4.4 config"
date: 2005-08-23
forum: Gaming &amp; Leisure
---

### Post by leezer3 on 2005-08-23
Hi guys,
What I need is pretty simple- I would like the base config that I have to stick into the Point2Play config file as per the setup guide (The PC I'm trying to install on has not net & no prospect of it :P). However, I can't seem to get it right, and I'm hoping that someone who has done it before can assist.

Cheers.

-Leezer-

---

### Post by NumbSkullMD on 2005-08-23
Here are the contents of my /usr/lib/transgaming_point2play/Point2PlayRC file...I assume that's what you want...

```
[winex]
default=4.0.1
<401f>4.0.1=/usr/lib/transgaming_cedega:/usr/bin/cedega
```

---

### Post by leezer3 on 2005-08-24
[QUOTE=NumbSkullMD]Here are the contents of my /usr/lib/transgaming_point2play/Point2PlayRC file...I assume that's what you want...

```
[winex]
default=4.0.1
<401f>4.0.1=/usr/lib/transgaming_cedega:/usr/bin/cedega
```[/QUOTE]
 Finally- I found it :D
The file must be named Point2PlayRC, WITH the capitalisation, otherwise Point2Play won't recognise it. What a waste of time & effort :rolleyes:

Thanks!

-Leezer-

---

