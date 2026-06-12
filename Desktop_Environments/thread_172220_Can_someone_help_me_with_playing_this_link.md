---
title: "Can someone help me with playing this link?"
date: 2006-05-08
forum: Desktop Environments
---

### Post by ViB on 2006-05-08
This is a mms broadcast radio i guess, and I've tried many players in Ubuntu, VLC, mplayer, Totem, xmms without success. It works fine in MS media player though. I use Breeze with the codecs installed by Automatix.
LBC radio link:
[mms://cpg-wm.interoutemediaservices.com/chrysalis/protected/lbc973.wma?tk=Rt%2FCBalAyAg=PXG3DJIGLceW2LUGaCOFrrGTuvo=*2]("mms://cpg-wm.interoutemediaservices.com/chrysalis/protected/lbc973.wma?tk=Rt%2FCBalAyAg=PXG3DJIGLceW2LUGaCOFrrGTuvo=*2")

---

### Post by mips on 2006-05-08
I get an error:
```

Totem could not play 'mms://cpg-
wm.interoutemediaservices.com/chrysalis/
protected/lbc973.wma?tk=Rt/
CBalAyAg=PXG3DJIGLceW2LUGaCOFrrGTuvo=*2'.

No URI handler implemented for "mms".
```

---

### Post by ViB on 2006-05-08
Well, in my case it's:
------------------------------------
Totem could not play 'mms://cpg-wm.interoutemediaservices.com/chrysalis/protected/lbc973.wma?tk=Rt/CBalAyAg=PXG3DJIGLceW2LUGaCOFrr GTuvo=*2'.

Failed to open media file; unknown error
-------------------------------------------

---

### Post by ViB on 2006-05-08
It seems they change the link sometimes... :-( So, please copy the link to test from their webpage [http://www.lbc973.co.uk/]("http://www.lbc973.co.uk/") ("Listen Live" button in the middle).

---

### Post by ububaba on 2006-05-09
[QUOTE=ViB]It seems they change the link sometimes... :-( So, please copy the link to test from their webpage [http://www.lbc973.co.uk/]("http://www.lbc973.co.uk/") ("Listen Live" button in the middle).[/QUOTE]
Sorry to say I used the link you provided. This is what I got. Any other solution?
[PHP]
Totem could not play 'mms://cpg-wm.interoutemediaservices.com/chrysalis/protected/lbc973.wma?tk=P0aLs9lByAg=i0/eh4ny/xBB1iM5SkHIsXd5S18=*2'.

The connection to this server was refused.[/PHP]

---

### Post by DoktorSeven on 2006-05-09
I got it to play using mplayer.  (Note I also have the win32codecs package installed, so that likely helps.)

---

