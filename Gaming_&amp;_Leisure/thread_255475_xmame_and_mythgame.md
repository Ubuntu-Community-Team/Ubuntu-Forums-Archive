---
title: "xmame and mythgame"
date: 2006-09-11
forum: Gaming &amp; Leisure
---

### Post by tbonius on 2006-09-11
I have noticed quote a few posts regarding the current version of xmame and mythgame in the apt repositories.

Currently I am running Myth 0.18 (I do not wish to upgrade to Myth 0.19 or even an SVN version at this time).  I installed the mythgame package and also installed xmame.  I had the infamous issue of "This version of xmame is not supported".  So I attempted to find an older deb package of xmame to install.  I finally found a breezy package (0.87) and installed it.  Now Mythgame works fine with xmame, but there is no native lirc support.

Apparently native lirc support is built into 0.90 (or 0.95?) and higher.  I tried to download that version of xmame and compile it but received quite a few errors during compilation:

```
src/config.c:643: warning: implicit declaration of function âXML_ParserFreeâ
make: *** [xmame.obj/config.o] Error 1
```

I have a two fold question.  What dependencies do I need inorder to compile xmame src.  If there is a prebuilt DEB package of xmame 0.95 or higher.. where can I get it from.

I really would enjoy getting xmame running natively with lirc so I can stop passing xmacroplay events via irexec to xmame.

Thanks

T

---

