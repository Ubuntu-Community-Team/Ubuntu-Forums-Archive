---
title: "installing theme from source"
date: 2007-08-26
forum: Desktop Effects &amp; Customization
---

### Post by bump_ on 2007-08-26
HI,

I am running kubuntu feisty. I downloaded a theme's source and tried to install it. After much googling, I finally reached the end of "make install" but I'm not really sure if it was successful.

Here is "make":
```
beast@beast-desktop:~/Desktop/domino-0.4$ make
make  all-recursive
make[1]: Entering directory `/home/beast/Desktop/domino-0.4'
Making all in domino
make[2]: Entering directory `/home/beast/Desktop/domino-0.4/domino'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/beast/Desktop/domino-0.4/domino'
Making all in dominoConfig
make[2]: Entering directory `/home/beast/Desktop/domino-0.4/dominoConfig'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/beast/Desktop/domino-0.4/dominoConfig'
Making all in client
make[2]: Entering directory `/home/beast/Desktop/domino-0.4/client'
Making all in .
make[3]: Entering directory `/home/beast/Desktop/domino-0.4/client'
make[3]: Nothing to be done for `all-am'.
make[3]: Leaving directory `/home/beast/Desktop/domino-0.4/client'
Making all in config
make[3]: Entering directory `/home/beast/Desktop/domino-0.4/client/config'
make[3]: Nothing to be done for `all'.
make[3]: Leaving directory `/home/beast/Desktop/domino-0.4/client/config'
make[2]: Leaving directory `/home/beast/Desktop/domino-0.4/client'
make[2]: Entering directory `/home/beast/Desktop/domino-0.4'
make[2]: Leaving directory `/home/beast/Desktop/domino-0.4'
make[1]: Leaving directory `/home/beast/Desktop/domino-0.4'

```

and here is "make install"
```
Making install in domino
make[1]: Entering directory `/home/beast/Desktop/domino-0.4/domino'
make[2]: Entering directory `/home/beast/Desktop/domino-0.4/domino'
make[2]: Nothing to be done for `install-exec-am'.
test -z "/usr/lib/kde3/plugins/styles" || mkdir -p -- "/usr/lib/kde3/plugins/styles"
 /bin/bash ../libtool --silent --mode=install /usr/bin/install -c -p  'domino.la' '/usr/lib/kde3/plugins/styles/domino.la'
PATH="$PATH:/sbin" ldconfig -n /usr/lib/kde3/plugins/styles
test -z "/usr/share/apps/kdisplay/color-schemes" || mkdir -p -- "/usr/share/apps/kdisplay/color-schemes"
 /usr/bin/install -c -p -m 644 'Domino.kcsrc' '/usr/share/apps/kdisplay/color-schemes/Domino.kcsrc'
test -z "/usr/share/apps/kstyle/themes" || mkdir -p -- "/usr/share/apps/kstyle/themes"
 /usr/bin/install -c -p -m 644 'domino.themerc' '/usr/share/apps/kstyle/themes/domino.themerc'
make[2]: Leaving directory `/home/beast/Desktop/domino-0.4/domino'
make[1]: Leaving directory `/home/beast/Desktop/domino-0.4/domino'
Making install in dominoConfig
make[1]: Entering directory `/home/beast/Desktop/domino-0.4/dominoConfig'
make[2]: Entering directory `/home/beast/Desktop/domino-0.4/dominoConfig'
test -z "/usr/lib/kde3" || mkdir -p -- "/usr/lib/kde3"
 /bin/bash ../libtool --silent --mode=install /usr/bin/install -c -p  'kstyle_domino_config.la' '/usr/lib/kde3/kstyle_domino_config.la'
PATH="$PATH:/sbin" ldconfig -n /usr/lib/kde3
make[2]: Nothing to be done for `install-data-am'.
make[2]: Leaving directory `/home/beast/Desktop/domino-0.4/dominoConfig'
make[1]: Leaving directory `/home/beast/Desktop/domino-0.4/dominoConfig'
Making install in client
make[1]: Entering directory `/home/beast/Desktop/domino-0.4/client'
Making install in .
make[2]: Entering directory `/home/beast/Desktop/domino-0.4/client'
make[3]: Entering directory `/home/beast/Desktop/domino-0.4/client'
test -z "/usr/lib/kde3" || mkdir -p -- "/usr/lib/kde3"
 /bin/bash ../libtool --silent --mode=install /usr/bin/install -c -p  'kwin3_domino.la' '/usr/lib/kde3/kwin3_domino.la'
PATH="$PATH:/sbin" ldconfig -n /usr/lib/kde3
test -z "/usr/share/apps/kwin" || mkdir -p -- "/usr/share/apps/kwin"
 /usr/bin/install -c -p -m 644 'domino.desktop' '/usr/share/apps/kwin/domino.desktop'
make[3]: Leaving directory `/home/beast/Desktop/domino-0.4/client'
make[2]: Leaving directory `/home/beast/Desktop/domino-0.4/client'
Making install in config
make[2]: Entering directory `/home/beast/Desktop/domino-0.4/client/config'
make[3]: Entering directory `/home/beast/Desktop/domino-0.4/client/config'
test -z "/usr/lib/kde3" || mkdir -p -- "/usr/lib/kde3"
 /bin/bash ../../libtool --silent --mode=install /usr/bin/install -c -p  'kwin_domino_config.la' '/usr/lib/kde3/kwin_domino_config.la'
PATH="$PATH:/sbin" ldconfig -n /usr/lib/kde3
make[3]: Nothing to be done for `install-data-am'.
make[3]: Leaving directory `/home/beast/Desktop/domino-0.4/client/config'
make[2]: Leaving directory `/home/beast/Desktop/domino-0.4/client/config'
make[1]: Leaving directory `/home/beast/Desktop/domino-0.4/client'
make[1]: Entering directory `/home/beast/Desktop/domino-0.4'
make[2]: Entering directory `/home/beast/Desktop/domino-0.4'
make[2]: Nothing to be done for `install-exec-am'.
make[2]: Leaving directory `/home/beast/Desktop/domino-0.4'
make[1]: Leaving directory `/home/beast/Desktop/domino-0.4'

```

I don't see any error messages in there but I don't know where it installed the theme to if it was successful.

---

### Post by Happy_Man on 2007-08-26
Yes, the make and make install were both successful. Go check and see whether it showed up. 

On a side note..... *ahem* Domino is available in the repos. It's in the KDE themes package, I think.

---

### Post by bump_ on 2007-08-27
But what would I have learned by downloading the .deb? :)

---

### Post by Happy_Man on 2007-08-27
Why one must never use Slackware? :D

---

### Post by bump_ on 2007-08-30
ok this may sound a bot dumb, but how do i access the theme? I tried going to "kcontrol" and "theme manager", but it doesn't show up. any help?

---

### Post by bump_ on 2007-08-30
ok, ignore the above question, I figured it out, but I have another now. I am installing the Dark Plastic 2 suite
[http://www.kde-look.org/content/show.php/Dark+Plastic+2+Suite?content=51302](http://www.kde-look.org/content/show.php/Dark+Plastic+2+Suite?content=51302)

and I got to this point in the instructions

"Copy the scheme files(Domino_versionrc) located in the Style/Domino folder to /YOUR_HOME/.qt/"

but for the life of me I cannot find the right directory. Can anyone help me?

---

### Post by FuturePilot on 2007-08-30
.qt is a hidden directory. All directories starting with a . are hidden. In Konqueror go View>Show Hidden Files.

---

