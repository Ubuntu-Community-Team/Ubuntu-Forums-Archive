---
title: "Error Compiling AWN"
date: 2008-01-27
forum: Desktop Effects &amp; Customization
---

### Post by denham2010 on 2008-01-27
Hi,

Hoping someone can help me solve this.

I have a fresh install of Xubuntu, and compiling most software from source throws the following error:

```
Making all in po
make[2]: Entering directory `~/avant-window-navigator-0.2.1/po'
file=`echo ar | sed 's,.*/,,'`.gmo \
          && rm -f $file &&  -o $file ar.po
/bin/sh: -o: not found

```

As you can see from this example, this one is AWN. I get very similar errors compiling the latest Xfce 4.4.2 from source.

Strange thing is, sudo make install works, and the apps work (as far as I can tell, no errors, crashing or segfaults). But my problem here is I would prefer to use checkinstall so all my software is registered in the package database.

I originally thought the problem may be /bin/sh using dash instead of bash, but changing this made no difference (although in a fresh install of Kubuntu it did fix the problem).

Can anyone provide (what is most probably the most simple thing I am overlooking) a solution?

Thanks.

---

### Post by denham2010 on 2008-01-27
First problem solved.

It appears I didn't have gettext installed. So now the make error does not happen.

New issue now, running checkinstall it ends up failing with the following:

```
ranlib /usr/local/lib/python2.5/site-packages/awn/awn.a
ranlib: could not create temporary file whilst writing archive: No more archived files

```

---

