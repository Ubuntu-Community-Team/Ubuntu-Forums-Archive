---
title: "Issues compiling cvscedega on breezy..."
date: 2005-10-17
forum: Gaming &amp; Leisure
---

### Post by deepspring on 2005-10-17
Hi Guys,

I am trying to get cvscedega installed on breezy. I have tried both of [these](http://www.frankscorner.org/index.php?p=cedegacvs) [two](http://www.linux-gamers.net/modules/wfsection/article.php?articleid=45) how-tos to the letter.

During the compile stage, both stop with the below quoted error:

```
.
.
.
gcc -MMD -c  -I. -I. -I../../include -I../../include  -g -O2 -Wall -mpreferred-stack-boundary=2 -fno-keep-static-consts -D__const=const -fno-strict-aliasing -D__int8=char -D__int16=short -D__int32=int "-D__int64=long long" -D__WINE__ -D_REENTRANT  -o newstruc.o newstruc.c
newstruc.c: In function ‘handle_ani_list’:
newstruc.c:740: error: invalid lvalue in increment
newstruc.c: In function ‘new_ani_curico’:
newstruc.c:851: error: invalid lvalue in increment
make[2]: *** [newstruc.o] Error 1
make[2]: Leaving directory `/temp/winex/tools/wrc'
make[1]: *** [wrc] Error 2
make[1]: Leaving directory `/temp/winex/tools'
make: *** [tools] Error 2

Compilation failed, aborting install.
```

Any help with this is appreciated.

Thanks

---

