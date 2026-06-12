---
title: "Problem installing bmp-itouch plugin"
date: 2005-10-14
forum: Desktop Environments
---

### Post by gflores on 2005-10-14
After extracting it and doing ./configure and then make, I get this in the terminal.

```

make  all-recursive
make[1]: Entering directory `/home/gabe/Desktop/bmp-itouch-1.0.1'
Making all in intl
make[2]: Entering directory `/home/gabe/Desktop/bmp-itouch-1.0.1/intl'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/gabe/Desktop/bmp-itouch-1.0.1/intl'
Making all in po
make[2]: Entering directory `/home/gabe/Desktop/bmp-itouch-1.0.1/po'
PATH=../src:$PATH /usr/bin/xgettext --default-domain=bmp-itouch --directory=.. \  --add-comments --keyword=_ --keyword=N_ \
  --files-from=./POTFILES.in \
&& test ! -f bmp-itouch.po \
   || ( rm -f ./bmp-itouch.pot \
        && mv bmp-itouch.po ./bmp-itouch.pot )
/bin/sh: /usr/bin/xgettext: No such file or directory
mv: cannot stat `bmp-itouch.po': No such file or directory
make[2]: *** [bmp-itouch.pot] Error 1
make[2]: Leaving directory `/home/gabe/Desktop/bmp-itouch-1.0.1/po'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/gabe/Desktop/bmp-itouch-1.0.1'
make: *** [all] Error 2

```

I guess I'm missing something (xgettext?), but I can't find xgettext in Synaptic. Thanks in advance.

---

### Post by Ampersand on 2005-10-14
Not sure what package contains it, but I seem to have it installed so it's somewhere in apt. (:

Try getting the xlibs and xlibs-dev packages. Also, make sure you've got the build-essential package.

---

### Post by gflores on 2005-10-14
Ok, well I installed gettext and ran make and it went through. However, the plugin doesn't work... Oh well.

---

