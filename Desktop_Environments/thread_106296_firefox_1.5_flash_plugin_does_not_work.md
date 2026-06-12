---
title: "firefox 1.5 flash plugin does not work"
date: 2005-12-20
forum: Desktop Environments
---

### Post by shizow on 2005-12-20
i installed ff 1.5 following everyhting from the wiki
[https://wiki.ubuntu.com/FirefoxNewVersion](https://wiki.ubuntu.com/FirefoxNewVersion)
but i dont get the flash plugin to work
when i try to load flash sites, just nothing happens

i deinstalled the flashplayer-mozilla plugin
and reinstalled it
and also tried the missing plguin installation which puts the flashplayer plugin into .mozilla/plugins

but nothing works

---

### Post by antidrugue on 2005-12-20
Does the flash plugins works in any other browser?

Did you do these steps correctly?
[LIST]
[*] Link to your plugins (and remove totem-mozilla as it doesn't seem to work with Firefox 1.5):  
  cd /opt/firefox/plugins/
 sudo ln -s /usr/lib/mozilla-firefox/plugins/* .
 sudo rm libtotem_mozilla.*[FONT=verdana,geneva,lucida,'lucida grande',arial,helvetica,sans-serif][/font][/LIST]Uninstalling and reinstalling a package? It won't change anything really.
Unless you uninstalled it like that:
```

sudo apt-get remove --purge flashplayer-mozilla

``` 
But anyway the solution is never to reinstall.

---

### Post by shizow on 2005-12-20
[QUOTE=antidrugue]Does the flash plugins works in any other browser?

Did you do these steps correctly?
[LIST]
[*] Link to your plugins (and remove totem-mozilla as it doesn't seem to work with Firefox 1.5):  
  cd /opt/firefox/plugins/
 sudo ln -s /usr/lib/mozilla-firefox/plugins/* .
 sudo rm libtotem_mozilla.*[FONT=verdana,geneva,lucida,'lucida grande',arial,helvetica,sans-serif][/font][/LIST]Uninstalling and reinstalling a package? It won't change anything really.
Unless you uninstalled it like that:
```

sudo apt-get remove --purge flashplayer-mozilla

``` 

But anyway the solution is never to reinstall.[/QUOTE]


yes i already did this steps

```

/opt/firefox/plugins$ ll
total 0
lrwxrwxrwx  1 root root 40 Dec 20 17:13 flashplayer.xpt -> /usr/lib/mozilla/plugins/flashplayer.xpt
lrwxrwxrwx  1 root root 42 Dec 20 17:13 libflashplayer.so -> /usr/lib/mozilla/plugins/libflashplayer.so
lrwxrwxrwx  1 root root 41 Dec 20 17:13 libjavaplugin.so -> /usr/lib/mozilla/plugins/libjavaplugin.so
lrwxrwxrwx  1 root root 41 Dec 20 17:13 libnullplugin.so -> /usr/lib/mozilla/plugins/libnullplugin.so
lrwxrwxrwx  1 root root 46 Dec 20 17:13 mplayerplug-in-gmp.so -> /usr/lib/mozilla/plugins/mplayerplug-in-gmp.so
lrwxrwxrwx  1 root root 47 Dec 20 17:13 mplayerplug-in-gmp.xpt -> /usr/lib/mozilla/plugins/mplayerplug-in-gmp.xpt
lrwxrwxrwx  1 root root 45 Dec 20 17:13 mplayerplug-in-qt.so -> /usr/lib/mozilla/plugins/mplayerplug-in-qt.so
lrwxrwxrwx  1 root root 46 Dec 20 17:13 mplayerplug-in-qt.xpt -> /usr/lib/mozilla/plugins/mplayerplug-in-qt.xpt
lrwxrwxrwx  1 root root 45 Dec 20 17:13 mplayerplug-in-rm.so -> /usr/lib/mozilla/plugins/mplayerplug-in-rm.so
lrwxrwxrwx  1 root root 46 Dec 20 17:13 mplayerplug-in-rm.xpt -> /usr/lib/mozilla/plugins/mplayerplug-in-rm.xpt
lrwxrwxrwx  1 root root 46 Dec 20 17:13 mplayerplug-in-wmp.so -> /usr/lib/mozilla/plugins/mplayerplug-in-wmp.so
lrwxrwxrwx  1 root root 47 Dec 20 17:13 mplayerplug-in-wmp.xpt -> /usr/lib/mozilla/plugins/mplayerplug-in-wmp.xpt
lrwxrwxrwx  1 root root 42 Dec 20 17:13 mplayerplug-in.so -> /usr/lib/mozilla/plugins/mplayerplug-in.so
lrwxrwxrwx  1 root root 43 Dec 20 17:13 mplayerplug-in.xpt -> /usr/lib/mozilla/plugins/mplayerplug-in.xpt
lrwxrwxrwx  1 root root 35 Dec 20 17:13 nphelix.so -> /usr/lib/mozilla/plugins/nphelix.so
lrwxrwxrwx  1 root root 36 Dec 20 17:13 nphelix.xpt -> /usr/lib/mozilla/plugins/nphelix.xpt

```

but i tried it again

and now i also tried to do the uninstall with purge and install it again
but again flash is not working

---

### Post by antidrugue on 2005-12-20
Maybe instead you could make a symlink for the whole plugin directory, at least that's what I do and I never had a problem.

******************
But, still notice that your symlinks are not pointing in the right direction, they are pointing to /usr/lib/mozilla/ instead of /usr/lib/mozilla-firefox/
******************


Are they red colored in the terminal? They shouldn't be.

Just do a symlink for the whole directory instead:
```

cd /opt/firefox
sudo rm -r plugins
sudo ln -s /usr/lib/mozilla-firefox/plugins plugins

``` 
And restart Firefox...

---

### Post by iam10ninjas on 2005-12-20
Check about:plugins to see if there are two versions of the plugin installed. I had the same problem and all it took was purging one of them to get it to work again.

---

### Post by shizow on 2005-12-20
[QUOTE=antidrugue]Maybe instead you could make a symlink for the whole plugin directory, at least that's what I do and I never had a problem.

******************
But, still notice that your symlinks are not pointing in the right direction, they are pointing to /usr/lib/mozilla/ instead of /usr/lib/mozilla-firefox/
******************


Are they red colored in the terminal? They shouldn't be.

Just do a symlink for the whole directory instead:
```

cd /opt/firefox
sudo rm -r plugins
sudo ln -s /usr/lib/mozilla-firefox/plugins plugins

``` 
And restart Firefox...[/QUOTE]


the links are not red colored
poiting to mozilla-firefox does not change anything
since flashplayer-mozilla installs itself into ../mozilla/plugins and makes symbolic link pointing from mozilla-firefox to mozilla

and linking the whole directory does not work either

---

### Post by shizow on 2005-12-20
[QUOTE=iam10ninjas]Check about:plugins to see if there are two versions of the plugin installed. I had the same problem and all it took was purging one of them to get it to work again.[/QUOTE]

there is only one flash plugin installed

---

### Post by antidrugue on 2005-12-20
I think we are trying in the wrong direction, the how you followed specified that /opt/firefox is not useful after the install...

You could always uninstall flash plugin

```
[FONT=monospace][/FONT]
sudo apt-get remove --purge flashplayer-mozilla

```

And install this one instead:
```

sudo apt-get install flashplugin-nonfree

```

Which is essentially the same thing, a packaged flash plugin from Macromedia.

Anyway, just for the record, here is how I installed Firefox 1.5 and I never had a problem:

Installation of Firefox 1.5:
        download the package from mozilla.org
        Then install:
                ```

                tar zxf firefox-1.5.tar.gz
                cd firefox
                rm plugins
                ln -s /usr/lib/mozilla/plugins plugins
                cd ..
                sudo cp -r firefox /usr/share/
                
```

Then make a shortcut for it in the Gnome/KDE menu.

---

### Post by shizow on 2005-12-20
[QUOTE=antidrugue]I think we are trying in the wrong direction, the how you followed specified that /opt/firefox is not useful after the install...

You could always uninstall flash plugin

```
[FONT=monospace][/FONT]
sudo apt-get remove --purge flashplayer-mozilla

```

And install this one instead:
```

sudo apt-get install flashplugin-nonfree

```

Which is essentially the same thing, a packaged flash plugin from Macromedia.

Anyway, just for the record, here is how I installed Firefox 1.5 and I never had a problem:

Installation of Firefox 1.5:
        download the package from mozilla.org
        Then install:
                ```

                tar zxf firefox-1.5.tar.gz
                cd firefox
                rm plugins
                ln -s /usr/lib/mozilla/plugins plugins
                cd ..
                sudo cp -r firefox /usr/share/
                
```

Then make a shortcut for it in the Gnome/KDE menu.[/QUOTE]


i tried the nonfree plugin, but to where is it installed, (not in the mozilla or mozilla-firefox plugins folder)
i found some files here
/var/lib/dpkg/info/flashplugin-nonfree.config
/var/lib/dpkg/info/flashplugin-nonfree.list
/var/lib/dpkg/info/flashplugin-nonfree.templates
/var/lib/dpkg/info/flashplugin-nonfree.postinst
/var/lib/dpkg/info/flashplugin-nonfree.prerm
/var/lib/dpkg/info/flashplugin-nonfree.postrm
/var/lib/dpkg/info/flashplugin-nonfree.conffiles
/var/lib/dpkg/info/flashplugin-nonfree.md5sum

and then how should i link this to firefox?

---

### Post by antidrugue on 2005-12-20
Well, the flashplugin-nonfree install itself for browsers automaticaly just like flashplugin-mozilla.

---

### Post by antidrugue on 2005-12-20
[quote=shizow]i tried the nonfree plugin, but to where is it installed, (not in the mozilla or mozilla-firefox plugins folder)
i found some files here
/var/lib/dpkg/info/flashplugin-nonfree.config
/var/lib/dpkg/info/flashplugin-nonfree.list
/var/lib/dpkg/info/flashplugin-nonfree.templates
/var/lib/dpkg/info/flashplugin-nonfree.postinst
/var/lib/dpkg/info/flashplugin-nonfree.prerm
/var/lib/dpkg/info/flashplugin-nonfree.postrm
/var/lib/dpkg/info/flashplugin-nonfree.conffiles
/var/lib/dpkg/info/flashplugin-nonfree.md5sum

and then how should i link this to firefox?[/quote]

And really, those are not the plugins file, they are just its install/uninstall info for itself, if you upgrade it or uninstall it. Linking them will do nothing.

---

### Post by shizow on 2005-12-20
[QUOTE=antidrugue]Well, the flashplugin-nonfree install itself for browsers automaticaly just like flashplugin-mozilla.[/QUOTE]

but nothing works with the nonfree plugin, firefox or konqueror both say that no flash plugin is installed, thats why i asked where to directory is, where the nonfree is installed, so that i can link to opt/firefox

---

### Post by antidrugue on 2005-12-20
[quote=shizow]but nothing works with the nonfree plugin, firefox or konqueror both say that no flash plugin is installed, thats why i asked where to directory is, where the nonfree is installed, so that i can link to opt/firefox[/quote] 
Well, maybe the solution would be to uninstall nonfree as well and to install manualy in /usr/lib/mozilla with the [ macromedia flash installer]("http://www.macromedia.com/shockwave/download/download.cgi?P1_Prod_Version=ShockwaveFlash").

It's not suppose to be complicated...

Try automatix maybe. (There is on for KDE and one for Gnome).
For [ Ubuntu]("http://ubuntuforums.org/showthread.php?t=66563&highlight=automatix")
For [ Kubuntu]("http://ubuntuforums.org/showthread.php?t=105343&highlight=automatix")

Anyway if you followed this: [https://wiki.ubuntu.com/FirefoxNewVersion]("https://wiki.ubuntu.com/FirefoxNewVersion")
you'll notice that /opt/firefox can even be erased, it is useless at the end.

---

### Post by shizow on 2005-12-22
ok i just installed automatix and with this firefox with plugins and now it works!!!

thanks for all the hints

---

### Post by antidrugue on 2005-12-22
Hehe cool. Finally ;)

---

