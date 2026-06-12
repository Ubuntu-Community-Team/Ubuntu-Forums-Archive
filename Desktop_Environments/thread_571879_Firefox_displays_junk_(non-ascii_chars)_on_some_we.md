---
title: "Firefox displays junk (non-ascii chars) on some webpages"
date: 2007-10-09
forum: Desktop Environments
---

### Post by kung fu buntu on 2007-10-09
Some webpages simply don't work with firefox. For a same domain some pages work others do not. Instead of getting text I get a bunch of non-ascii chars. Examples:
(note I'm posting here with Opera... characters where translated to Japanese)

[https://retailer.echostar.com/prmportal/](https://retailer.echostar.com/prmportal/)
```
&#15464;&#29805;&#27710;&#3338;&#3338;&#15464;&#25953;&#25662;&#3338;&#15475;&#25458;&#26992;&#29758;&#3338;&#26229;&#28259;&#29801;&#28526;&#8263;&#28532;&#28501;&#29292;&#10357;&#29292;&#10509;&#2683;&#3338;&#8224;&#8308;&#26729;&#29486;&#27759;&#25441;&#29801;&#28526;&#8253;&#8309;&#29292;&#15117;&#2685;&#3338;&#15407;&#29539;&#29289;&#28788;&#15885;&#2620;&#12136;&#25953;&#25662;&#3338;&#3338;&#15458;&#28516;&#31008;&#28526;&#19567;&#24932;&#15650;&#18287;&#29807;&#21874;&#27688;&#10099;&#29793;&#29300;&#11891;&#30565;&#16211;&#22341;&#17261;&#25661;&#21364;&#24946;&#29735;&#10530;&#15885;&#2620;&#12130;&#28516;&#31038;&#3338;&#3338;&#15407;&#26740;&#28012;
```

[http://www.coldplay.com/forum.htm](http://www.coldplay.com/forum.htm)
```
forum.htm&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;TEXTttxt&#65533;ÿÿÿÿ&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#8249;&#65533;&#65533;
```

This sucks... what am I missing here?

---

### Post by rfruth on 2007-10-09
The 1st link = The server you are accessing is either busy or experiencing difficulties. Please close the web browser, start a new one and try logging in again. For further support, please copy and send the full message text to your system administrator.[20:33:19]

---

### Post by kung fu buntu on 2007-10-10
I can't believe nobody had this problem before...
What about the 2nd site... What about this one [http://secure.b-on.pt/V/?func=meta-1](http://secure.b-on.pt/V/?func=meta-1)

thanks

---

### Post by rfruth on 2007-10-10
Now Firefox 2.x reports (for 1st link) This XML file does not appear to have any style information associated with it - secure.b link okay for me. Any flash, Java problems, your Firefox profile okay :confused:

---

### Post by kung fu buntu on 2007-10-11
Everything works fine with Opera... It's just this crazy firefox :mad:

Another one that fails:
[http://www.forbes.com/feeds/ap/2007/10/11/ap4211646.html](http://www.forbes.com/feeds/ap/2007/10/11/ap4211646.html)
[http://www.picoodle.com/](http://www.picoodle.com/)
[[img]http://img3.freeimagehosting.net/uploads/th.eb77f75d9f.jpg[/img]](http://img3.freeimagehosting.net/image.php?eb77f75d9f.jpg)

I doubt it's flash or anything else...

I can access sites like these below with no problems:
[http://starcraft2.com/](http://starcraft2.com/)
[http://finance.google.com/finance?q=goog](http://finance.google.com/finance?q=goog)

---

### Post by kung fu buntu on 2007-10-25
Anybody?

---

### Post by kung fu buntu on 2007-10-30
OK, I figured out what the problem was. It has to do with the "character encoding system". I changed it from UTF-16 to ISO-8859-15 and most sites are working fine.
However, sites like this [http://www.coldplay.com/forum.htm](http://www.coldplay.com/forum.htm) still fails miserably.

Any idea on how to fix the problem permanently?

---

### Post by carlos1992 on 2007-10-30
hey maybe is just the servers cuz i visited the forbes link and was ok i use FF maybe checking in the content section (-->edit-->content) and see if there's one with check (all must be checked)

---

