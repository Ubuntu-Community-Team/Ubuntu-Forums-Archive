---
title: "grep, sed, script, how-to ?!"
date: 2009-02-25
forum: General Help
---

### Post by paddy_1 on 2009-02-25
Hello,

I'm having following text, and I want to figure out the myspace.com links in such a form like this "www.mysace.com/123abc".

```
Unter www.myspace.com/damiensound kÃ¶nnt ihr euch schon mal einen Eindruck von uns machen.
Unter www.myspace.com/damiensound kÃ¶nnt ihr euch schon mal einen Eindruck von uns machen.<br />
www.myspace.com/jimjackmusic
www.myspace.com/jimjackmusic<br />
Die Termine wären immer Donnerstag bis samstags evtl. auch Sonntags, wenn es sich anders nicht vereinbaren lässt. Soundbeispiele findet man vorab unter www.Chasing4glory.de oder unter www.myspace.com/chasinforglory. Bitte gebt uns bzw. mir ein kurzes Feedback, wann bei euch Termine frei wären.
Die Termine w&auml;ren immer Donnerstag bis samstags evtl. auch Sonntags, wenn es sich anders nicht vereinbaren l&auml;sst. Soundbeispiele findet man vorab unter www.Chasing4glory.de oder unter www.myspace.com/chasinforglory. Bitte gebt uns bzw. mir ein kurzes Feedback, wann bei euch Termine frei w&auml;ren.<br />
Murdock:http://www.myspace.com/murdockband  + TrustingNolan: http://www.myspace.com/trustingnolan  + BLONK: http://www.myspace.com/blonkvshometown
Murdock:http://www.myspace.com/murdockband  + TrustingNolan: http://www.myspace.com/trustingnolan  + BLONK: http://www.myspace.com/blonkvshometown<br />
Hallo, ich bin da Heimo. Spiele Schlagzeug bei First Class (http://www.myspace.com/firstclassmpc). Wir wÃŒrden sehr gern mal in MÃŒnchen/Umgebung spielen. Kannst du uns da weiterhelfen?
<td valign="top">Hallo, ich bin da Heimo. Spiele Schlagzeug bei First Class (http://www.myspace.com/firstclassmpc). Wir wÃŒrden sehr gern mal in MÃŒnchen/Umgebung spielen. Kannst du uns da weiterhelfen?<br />
band website: http://www.myspace.com/smokeboxband
band website: http://www.myspace.com/thepoweronoffs
www.myspace.com/anewdayuk
www.myspace.com/standfast0815
www.myspace.com/IncisionBooking
www.myspace.com/anewdayuk
www.myspace.com./goodlookingtrash
www.myspace.com/standfast0815
font-size: 11pt;"><a href=3D"http://www.myspace.com/anewdayuk">www.myspace.=
font-size: 11pt;"><a href=3D"http://www.myspace.com/standfast0815">www.mysp=
www.IncisionBooking.com</a><br><a href=3D"http://www.myspace.com/IncisionBo=
oking">www.myspace.com/IncisionBooking</a><br>
=3D"http://www.myspace.com/anewdayuk">www.myspace.com/anewdayuk</a><br><br>=
www.myspace.com./goodlookingtrash<br> &nbsp;<br>Inglow (NOR)<br>Rock, Alter=
and Fast <br>Posthardcore <br><a href=3D"http://www.myspace.com/standfast08=
15">www.myspace.com/standfast0815</a> <br><br>The Autumn's Regret<br>Scream=
> darüber freuen. Auf www.myspace.com/dwfband.com kann man sich etwas 
http://www.myspace.com/delikat
www.myspace.com/tesseract
Web: www.myspace.com/manusbooking
www.myspace.com/obliqonline
www.myspace.com/finaldayssociety
www.myspace.com/ehnahremetal
www.myspace.com/in_mourning
www.myspace.com/youleftmebreathless
www.myspace.com/enemyisus
www.myspace.com/leechofficial
size=3D3>www.myspace.com/tesseract</FONT></A><BR><BR><BR><FONT=20
size=3D3>www.myspace.com/manusbooking</FONT></A><BR><FONT face=3D"Times =
size=3D3>www.myspace.com/obliqonline</FONT></A><BR><FONT face=3D"Times =
size=3D3>www.myspace.com/finaldayssociety</FONT></A><BR><FONT=20
size=3D3>www.myspace.com/ehnahremetal</FONT></A><BR><FONT face=3D"Times =
size=3D3>www.myspace.com/in_mourning</FONT></A><BR><FONT=20
size=3D3>www.myspace.com/youleftmebreathless</FONT></A><BR><FONT=20
size=3D3>www.myspace.com/enemyisus</FONT></A><BR><FONT face=3D"Times New =
size=3D3>www.myspace.com/leechofficial</FONT></A><BR><BR></FONT></DIV></B=
```

---

### Post by Lars Stokholm on 2009-02-25
Will this do?```
grep -o myspace.com/[a-Z]* yourtextfile
```

---

### Post by paddy_1 on 2009-02-25
thanks a lot, it works,
finally I removed the lines wich appear twice with 'sort -u'

```
grep -o myspace.com/[a-Z]* Myspace.txt | sort -u > ~/bands.txt

```

---

