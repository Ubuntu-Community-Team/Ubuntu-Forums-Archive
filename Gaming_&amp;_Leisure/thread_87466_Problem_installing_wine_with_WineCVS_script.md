---
title: "Problem installing wine with WineCVS script"
date: 2005-11-08
forum: Gaming &amp; Leisure
---

### Post by trian on 2005-11-08
When I try to install cedegacvs through wineCVS script thats is available. I get this error message, I have installed all the compilers that is needed

```

NTRANT  -o newstruc.o newstruc.c
newstruc.c: In function ‘handle_ani_list’:
newstruc.c:740: error: invalid lvalue in increment
newstruc.c: In function ‘new_ani_curico’:
newstruc.c:851: error: invalid lvalue in increment
make[2]: *** [newstruc.o] Error 1
make[2]: Leaving directory `/root/.WineCVS/sources/cvscedega/winex/tools/wrc'
make[1]: *** [wrc] Error 2
make[1]: Leaving directory `/root/.WineCVS/sources/cvscedega/winex/tools'
make: *** [tools] Error 2


Error in Make

Try fixing the error based on the output above, and
run the script again, without paramaters (Eg: WineCVS.sh)


```

Oh. and yes, I ran it without parameters.

---

### Post by trian on 2005-11-08
Ooh. forget it.


Found this site. Nice guide.

[http://www.linux-gamers.net/modules/wfsection/article.php?articleid=45](http://www.linux-gamers.net/modules/wfsection/article.php?articleid=45)

EDIT:

Didn't work after all.

EDIT2: 

Now I'm trying this. Google is my friend

[http://ubuntuforums.org/showthread.php?t=76077](http://ubuntuforums.org/showthread.php?t=76077)

EDIT3:
This did the trick :)

---

