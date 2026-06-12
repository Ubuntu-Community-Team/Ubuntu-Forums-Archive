---
title: "Evolution and duplicate messages"
date: 2007-03-14
forum: Desktop Environments
---

### Post by akvik on 2007-03-14
Hi,

I found a plugin for evolution that finds duplicate messages, called remove-duplicates-plugin:
[http://www.advogato.org/person/garnacho/diary.html](http://www.advogato.org/person/garnacho/diary.html)

I tried to install it, but I get the following error running ./configure:

```

configure: error: Package requirements (
                  evolution-plugin-2.4 >= 2.3.2
                  ) were not met.
Consider adjusting the PKG_CONFIG_PATH environment variable if you
installed software in a non-standard prefix.

```

It seems my evolution-plugins package is too new for the plugin, or that the package name is different (in synaptic it's called evolution-plugins). 

Does anyone know if there is a package for ubuntu already for this plugin?

---

### Post by nab on 2007-11-01
well,
I don't know wheather this is still needed, but I got the plugin working:

I got the rpm from:
[http://rpm.pbone.net/index.php3/stat/4/idpl/5184826/com/evolution-remove-duplicates-0.0.3-1.fc8.i386.rpm.html](http://rpm.pbone.net/index.php3/stat/4/idpl/5184826/com/evolution-remove-duplicates-0.0.3-1.fc8.i386.rpm.html)

and build with alien a deb and installed.

I attached my deb for your convenience :-)
Niko

---

### Post by harce on 2007-11-15
[http://www.gnome.org/~carlosg/stuff/evolution/](http://www.gnome.org/~carlosg/stuff/evolution/)

found thous, but couldent compile it ( "error: C compiler cannot create executables" o0 )
the deb package posted above gives a "dependency is not satisfiable: libc6" although I got it...   still thanks for you work!

---

### Post by pmorton on 2007-11-17
> **nab said:**
> well,
I don't know wheather this is still needed, but I got the plugin working:

I got the rpm from:
[http://rpm.pbone.net/index.php3/stat/4/idpl/5184826/com/evolution-remove-duplicates-0.0.3-1.fc8.i386.rpm.html](http://rpm.pbone.net/index.php3/stat/4/idpl/5184826/com/evolution-remove-duplicates-0.0.3-1.fc8.i386.rpm.html)

and build with alien a deb and installed.

I attached my deb for your convenience :-)
Niko

Thanks so much, Nab. I'd  just about given up hunting for a duplicate removal plug-in that works with Evolution 2.12, when I came across your post. Brilliant.

---

### Post by miaviator278 on 2007-12-18
you need to install the evolution-dev package in order to have the necessary pkgconfig files.

```
sudo apt-get install  evolution-dev
```

I have attached a .deb of the newest version.

---

### Post by MustNotSleep on 2008-01-07
> **miaviator278 said:**
> you need to install the evolution-dev package in order to have the necessary pkgconfig files.

```
sudo apt-get install  evolution-dev
```

I have attached a .deb of the newest version.
really? can i see the changelog, please? it being double in size, and all..

---

### Post by sfh1975 on 2008-01-21
hi folks
i am sorry but how do you run that duplicate-remover?
i have it installed in evolution but dont find anything to click and get rid of dupes.
much obliged,

---

### Post by geoffatmk on 2008-03-19
Not sure if anyone has responded to you or if you still need it.

Just highlight (select) the emails you want to check, right click and at the bottom of the list is "Remove Duplicates"

BTW thanks from me too nab.  Your deb worked for me when ./configure was driving me up the proverbial wall over dependencies and missing files.

Geoff

---

### Post by FadeFX on 2008-03-29
thanx man, this one worked fine for me...

---

### Post by frogotronic on 2008-04-07
Thank you, thank you, thanks!


                       :guitar:


- CH

---

### Post by Misterium on 2008-06-20
Hello, I'm new to this forum (and a noob).
I installed the .deb file. But what should I do now? I did not know how to remove the duplicates in Evolution. Where did I install the deb packet?
Thx.

---

### Post by frogotronic on 2008-06-20
> **Misterium said:**
> Hello, I'm new to this forum (and a noob).
I installed the .deb file. But what should I do now? I did not know how to remove the duplicates in Evolution. Where did I install the deb packet?
Thx.

nothing.  if you installed the deb, it automatically knows where to install and setup everything and integrate into evolution.  You should now see a "remove duplicates" option in the menu when you right click on a message - see screenshot.

- CH

---

### Post by david.rahrer on 2008-06-27
I had trouble with the ones attached above using Hardy i386.  I've attached one I converted using alien (never could get it to build from source) from the latest rpm and it works perfectly for me.  Make sure you restart Evolution before expecting the remove duplicates option to show up as pictured above.

HTH someone!

---

