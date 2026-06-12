---
title: "java plugin"
date: 2005-04-16
forum: Desktop Environments
---

### Post by lmellen on 2005-04-16
I have the java plugin sitting in /usr/java/jrei.5.0_02/plugin. Both Firefox & Konqueror report the plugin missing. Do I have to install this with apt-get(aptitude)? Again, not a massive problem, but I would like to fix it.
                                                                     Larry :smile:

---

### Post by UbuWu on 2005-04-16
For firefox, try this:

sudo ln -s /usr/java/jre1.5.0_02/plugin/i386/ns7/libjavaplugin_oji.so /usr/lib/mozilla/plugins/
sudo ln -s /usr/java/jre1.5.0_02/plugin/i386/ns7/libjavaplugin_oji.so /usr/lib/mozilla-firefox/plugins/

---

### Post by lmellen on 2005-04-16
Ubuwu - Thanks for e reply -- :smile: 
 I get this message at prompt:
`/usr/lib/mozilla-firefox/plugins//libjavaplugin_oji.so': File exists.
The file exists, but the plugin is not working.-- Thanks again -- Larry

---

### Post by KLineD on 2005-05-14
I have the same problem, I'm using the JRE that comes with the SDK. The links are all there, even the one in /etc/alternatives

The only plugin that firefox reports is the flash plugin which is in the hidden folder .mozilla/plugins so I also copied the java plugin to that folder but firefox still doesn't recognize the plugin.

It's weird because previous to a firefox update, the plugin was working fine. I also tried installing a separate JRE with it's own plugin but I got the same results.

---

### Post by treris on 2005-05-15
I have the same problem, I've updated firefox from 1.0.2 to 1.0.4 but now whatever I do I'm not getting the java plugin to work

very annoying since it was working fine with firefox 1.0.2

---

### Post by usererror on 2005-05-16
that is weird.  I installed the java plugin manually.  I just downloaded the tar.gz file from sun's website and followed the instructions exactly.

apt-get will not install the plugin correctly, it has to be installed manually.

where did you install firefox to?

i installed mine to /usr/local/mozilla/firefox

assuming yours is in the same place your sym link for the plugin would look like:

**sudo ln -s /usr/java/jre1.5.0_02/plugin/i386/ns7/libjavaplugin_oji.so /usr/local/mozilla/firefox/plugins**

hope that helps!

---

### Post by bored2k on 2005-05-16
Why don't you guys make a .deb package from j2re ? the symlink gets done automatically :D.

sudo apt-get install fakeroot java-common java-package build-essential
fakeroot make-jpkg thenameofthesunj2repackage.bin
a .deb will be made, then
sudo dpkg -i filename.deb

---

### Post by usererror on 2005-05-16
[QUOTE=bored2k]Why don't you guys make a .deb package from j2re ? the symlink gets done automatically :D.

sudo apt-get install fakeroot java-common java-package build-essential
fakeroot make-jpkg thenameofthesunj2repackage.bin
a .deb will be made, then
sudo dpkg -i filename.deb[/QUOTE]

will that work?  what if people install mozilla firefox to different place?  would the package automatically locate the location of the plugins folder?

---

### Post by bored2k on 2005-05-16
[QUOTE=usererror]will that work?  what if people install mozilla firefox to different place?  would the package automatically locate the location of the plugins folder?[/QUOTE]
 Yes it works I have done this like 10 times now. Will it work if you manually installed a downloaded .bin from mozilla.org ? Simple, copy the java link from /usr/lib/mozilla-firefox/plugins to your /firefox/plugins/ directory.

[http://www.ubuntulinux.org/wiki/Java](http://www.ubuntulinux.org/wiki/Java)

---

### Post by jodef on 2005-05-16
[QUOTE=bored2k]Why don't you guys make a .deb package from j2re ? the symlink gets done automatically :D.

sudo apt-get install fakeroot java-common java-package build-essential
fakeroot make-jpkg thenameofthesunj2repackage.bin
a .deb will be made, then
sudo dpkg -i filename.deb[/QUOTE]Hey thanks for the info I must try that. :)

---

