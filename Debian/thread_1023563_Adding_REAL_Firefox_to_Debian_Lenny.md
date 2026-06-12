---
title: "Adding REAL Firefox to Debian Lenny"
date: 2008-12-28
forum: Debian
---

### Post by wolfen69 on 2008-12-28
[http://lxer.com/module/newswire/ext_link.php?rid=114153](http://lxer.com/module/newswire/ext_link.php?rid=114153)

i just did it and it works great. i couldn't stand the fonts in iceweasel.

---

### Post by jim_p on 2008-12-28
Well you can always download the source code (~50MB) and compile yourself with these very few parameters, make a deb and install. 

```
Configure arguments
--enable-application=xulrunner --prefix=/usr --with-default-mozilla-five-home=/usr/lib/xulrunner-1.9 --enable-default-toolkit=cairo-gtk2 --enable-pango --enable-xft --disable-freetype2 --enable-system-cairo --with-system-png --with-system-jpeg --with-system-zlib --with-system-bz2 --with-gssapi=/usr --with-system-nspr --with-system-nss --enable-xinerama --enable-single-profile --disable-profilesharing --enable-svg --enable-svg-renderer=cairo --enable-mathml --disable-pedantic --disable-long-long-warning --enable-gnomevfs --enable-gnomeui --disable-tests --disable-mochitest --disable-debug --enable-canvas --enable-js-binary --with-readline '--enable-extensions=default cookie permissions python/xpcom spellcheck' --disable-installer --disable-javaxpcom --disable-elf-dynstr-gc --enable-system-hunspell --disable-crashreporter --enable-system-sqlite --enable-system-lcms --disable-strip --disable-install-strip --enable-url-classifier --enable-startup-notification --host=i486-linux-gnu --build=i486-linux-gnu 
```

Plus, you can use the parameter --enable-official-branding to have the original icons that ff uses.

The method posted on that site defies apt, which is really dangerous. Not to mention that ff with every newer release depends on the equally newer release of xul-runner.

As for the fonts, I installed Tahoma from a windows pc and now ALL pages look much better with any browser.

---

