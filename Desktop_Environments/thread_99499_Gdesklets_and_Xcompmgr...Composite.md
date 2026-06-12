---
title: "Gdesklets and Xcompmgr...Composite"
date: 2005-12-05
forum: Desktop Environments
---

### Post by burnhamd on 2005-12-05
I installed the Composite manager and it works like a charm wonderful graphics. Very nice.  But when I run my translucent Gdesklets(enabling xcomposite translucency) backgrounds of my gdesklets are black.  I read somewhere that this might happen if the composite manager is not set up correctly but I cannot find any mistake.  I tried compiling metacity to see if that was the problem but it wouldnt config. I get this error:
```
checking for METACITY_MESSAGE... configure: error: Package requirements (gtk+-2.0 >= 2.6.0) were not met.
Consider adjusting the PKG_CONFIG_PATH environment variable if you
installed software in a non-standard prefix.

Alternatively you may set the METACITY_MESSAGE_CFLAGS and METACITY_MESSAGE_LIBS environment variables
to avoid the need to call pkg-config.  See the pkg-config man page for
more details.
```

does anyone know how I can get these gtk dev files or an alternative solution to my problem

Thanks in Advance

---

### Post by MetalMusicAddict on 2005-12-05
Ive had the same problem on 3 PCs. Best to post/read [THIS]("http://ubuntuforums.org/showthread.php?t=75527&highlight=composite") thread.

---

### Post by RAOF on 2005-12-05
[QUOTE=burnhamd]...does anyone know how I can get these gtk dev files or an alternative solution to my problem...[/QUOTE]

You can use
```
sudo apt-get build-dep metacity
``` to install all the build-dependencies of metacity.  Apt-get is awesome! :cool:

---

