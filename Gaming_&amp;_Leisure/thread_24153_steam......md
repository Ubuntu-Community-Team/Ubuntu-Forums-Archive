---
title: "steam.....?"
date: 2005-04-05
forum: Gaming &amp; Leisure
---

### Post by bibaleebu on 2005-04-05
is it possible to install steam in linux....I luv steam, and have been missing it scince i switch to linux.  Please let me know if there is anyway to do this! :mrgreen:

---

### Post by jdodson on 2005-04-05
[QUOTE=bibaleebu]is it possible to install steam in linux....I luv steam, and have been missing it scince i switch to linux.  Please let me know if there is anyway to do this! :mrgreen:[/QUOTE]

sure.  snag a copy of cedega, a transgaming product and install it that way.

i ran halflife2 on my hoary machine last night.

---

### Post by bibaleebu on 2005-04-05
thanks, but do you know of any free alternatives?

---

### Post by jdodson on 2005-04-05
[QUOTE=bibaleebu]thanks, but do you know of any free alternatives?[/QUOTE]

cedega from cvs.

---

### Post by bibaleebu on 2005-04-06
could you tell me how to set it up?

---

### Post by bored2k on 2005-04-06
[QUOTE=bibaleebu]could you tell me how to set it up?[/QUOTE]
 [http://www.linux-gamers.net/modules/wfsection/article.php?articleid=45](http://www.linux-gamers.net/modules/wfsection/article.php?articleid=45)

edit > By the way, some members are whining that the titles are somewhat vague and uninformative, so next time try naming your thread a little bit better ;) (help me, help you).

---

### Post by bibaleebu on 2005-04-06
ok, i will from now on. anyways, i followed that tut, but then when i got to the make stage, it went on for a while then had this error....


ts_xlib.c:1201: error: syntax error before '*' token
ts_xlib.c:1203: error: syntax error before '*' token
ts_xlib.c: In function `TS_XInitImageFuncPtrs':
ts_xlib.c:1206: error: `a0' undeclared (first use in this function)
make[1]: *** [ts_xlib.o] Error 1
make[1]: Leaving directory `/root/.WineCVS/sources/cvscedega/winex/tsx11'
make: *** [tsx11/libwine_tsx11.so] Error 2


Error in Make

Try fixing the error based on the output above, and
run the script again, without paramaters (Eg: WineCVS.sh)

---

### Post by bibaleebu on 2005-04-06
nvm, i got it to work, thank you soooo much :razz: i love you all....... :razz:

---

### Post by Beire on 2005-04-07
[QUOTE=bibaleebu]nvm, i got it to work, thank you soooo much :razz: i love you all....... :razz:[/QUOTE]
 you got steam to work with the cvs version ?

I didn't manage to get that working. It uodates fine on first launch but it just won't connect to my account. Always gives me the "Could not connect to Steam network s***"

All works fine in windooz

---

### Post by bibaleebu on 2005-04-07
no, i look ed around and found a deb package of 4.3, and used it....

---

