---
title: "Checkinstall failed for Avant-Window-Navigator on Feisty"
date: 2007-10-20
forum: Desktop Effects &amp; Customization
---

### Post by MeanderingCode on 2007-10-20
Hello, all.

I would like anyone's input on my problem here.

i followed AWN's guide [here]("http://awn.wetpaint.com/page/UbuntuFeistyHowTo?t=anon") for compiling their trunk on Ubuntu, wgetting their trunk build (date of this post) because they claim not to have a stable one.

Autogen.sh went fine, make went find, but checkinstall failed.  I've attached a text file of the output in an archive (23 kb text file, so i had to archive it because of forums size restrictions per type), but the end of the output is below:

```
/usr/bin/install -c .libs/awn.soT /usr/local/lib/python2.5/site-packages/awn/awn.so
/usr/bin/install: setting permissions for `/usr/local/lib/python2.5/site-packages/awn/awn.so': No such file or directory
/usr/bin/install -c .libs/awn.lai /usr/local/lib/python2.5/site-packages/awn/awn.la
/usr/bin/install: setting permissions for `/usr/local/lib/python2.5/site-packages/awn/awn.la': No such file or directory
/usr/bin/install -c .libs/awn.a /usr/local/lib/python2.5/site-packages/awn/awn.a
/usr/bin/install: setting permissions for `/usr/local/lib/python2.5/site-packages/awn/awn.a': No such file or directory
chmod 644 /usr/local/lib/python2.5/site-packages/awn/awn.a
ranlib /usr/local/lib/python2.5/site-packages/awn/awn.a
ranlib: could not create temporary file whilst writing archive: No more archived files
make[2]: *** [install-pyawnexecLTLIBRARIES] Error 1
make[2]: Leaving directory `/home/myself/tmp/avant-window-navigator/pyawn'
make[1]: *** [install-am] Error 2
make[1]: Leaving directory `/home/myself/tmp/avant-window-navigator/pyawn'
make: *** [install-recursive] Error 1

****  Installation failed. Aborting package creation.
```

Anyone with the time and knowledge to peruse and give me help or advice is most appreciated.

BTW: this was attempted after following the [HOWTO: Functional eyecandy with Avant Window Navigator and Affinity]("http://ubuntuforums.org/showthread.php?t=385981") post, which notes that the Feisty packages are no longer updated.

Many thanks.

---

