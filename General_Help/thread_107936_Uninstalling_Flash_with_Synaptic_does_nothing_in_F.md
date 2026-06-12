---
title: "Uninstalling Flash with Synaptic does nothing in Firefox"
date: 2005-12-24
forum: General Help
---

### Post by Fearan on 2005-12-24
I have been experiencing major problems with flash in firefox for quite some time now.  I have tried to uninstall and reinstall some things in Synaptic to remedy the problem, such as all the swf packages, and even firefox, but to no avail.  Problems I am experiencing include crashing, freezing, processor-hogging, etc.  I even have every flash item uninstalled right now, but firefox still is able to load any flash program.  Yet it is still experiencing the same problems when it comes across a website that integrates flash into its usage.  Any suggestions?  Macromedia.com says I am running version 7.0.25.0 of Flash, if that helps.  [IMG]http://img492.imageshack.us/img492/4104/screenshot1copy0xx.png[/IMG]

---

### Post by AmboyGuy on 2005-12-24
You have to find your Firefox executable directory and get into plugins directory and delelete the flashplayer plugin.
Mine is /opt/firefox/plugins ( I'm using FF 1.5 ) I don't remember where the 1.0.7 version is located.

---

### Post by kaamos on 2005-12-24
[QUOTE=AmboyGuy]I don't remember where the 1.0.7 version is located.[/QUOTE]

It's a symlink /usr/lib/mozilla-firefox/plugins/flashplayer.xpt that points to 
/usr/lib/mozilla/plugins/flashplayer.xpt

Your plugin in 1.5 probably also points to the same file.

---

### Post by Fearan on 2005-12-24
[QUOTE=AmboyGuy]You have to find your Firefox executable directory and get into plugins directory and delelete the flashplayer plugin.
Mine is /opt/firefox/plugins ( I'm using FF 1.5 ) I don't remember where the 1.0.7 version is located.[/QUOTE]
How do you upgrade to 1.5, anyway? is there a package for it?

---

### Post by Fearan on 2005-12-24
[QUOTE=kaamos]It's a symlink /usr/lib/mozilla-firefox/plugins/flashplayer.xpt that points to 
/usr/lib/mozilla/plugins/flashplayer.xpt

Your plugin in 1.5 probably also points to the same file.[/QUOTE]
I didn't find flashplayer.xpt in either directory.

---

### Post by kaamos on 2005-12-24
You are using 1.0.7 right? If there is no such file, you should have no flash plugin. Could you tell me what is the output of "ls -la /usr/lib/mozilla-firefox/plugins/"

This is assuming your firefox is a standard install from ubuntu repositories.

---

### Post by Fearan on 2005-12-24
[QUOTE=kaamos]You are using 1.0.7 right? If there is no such file, you should have no flash plugin. Could you tell me what is the output of "ls -la /usr/lib/mozilla-firefox/plugins/"

This is assuming your firefox is a standard install from ubuntu repositories.[/QUOTE]
I am using Firefox 1.0.7-0ubuntu20 as installed from synaptic.  Here is what you requested:
```
fearan@g-velocity:~$ ls -la /usr/lib/mozilla-firefox/plugins/
total 33
drwxr-xr-x   2 root root   256 2005-12-24 11:20 .
drwxr-xr-x  11 root root  1256 2005-12-24 12:33 ..
lrwxrwxrwx   1 root root    54 2005-11-25 17:38 libjavaplugin_oji.so -> /etc/alternatives/libjavaplugin_oji_mozilla_firefox.so
lrwxrwxrwx   1 root root    42 2005-10-26 17:59 libnpsoplugin.so -> ../../openoffice2/program/libnpsoplugin.so
-rw-r--r--   1 root root 24824 2005-09-22 14:46 libtotem_mozilla.so
-rw-r--r--   1 root root   168 2005-09-22 14:46 libtotem_mozilla.xpt
lrwxrwxrwx   1 root root    39 2005-09-14 19:41 nphelix.xpt -> /usr/bin/RealPlayer/mozilla/nphelix.xpt
lrwxrwxrwx   1 root root    50 2005-11-25 17:15 nppdf.so -> ../../Adobe/Acrobat7.0/Browser/intellinux/nppdf.so

```

---

### Post by kaamos on 2005-12-24
Hmm.. that means you should have no flash. Could you also post the output of "dpkg -l | grep flash"

---

### Post by Fearan on 2005-12-24
sorry, can't... something ironic just happened! My ubuntu's network configs were damaged beyond repair... that's why i didn't respond for so long.  i am now backing up my home folder via the livecd (what i absolutely need) and reinstalling ubuntu.  It needs a fresh start anyway... I think I did a very dirty upgrade when the breezy preview came out, and it's about time i did this anyway.  So i suspect i won't need to do anything to get rid of flash at this point! Thanks anyway.

---

### Post by TimelessRogue on 2005-12-24
I found the easiest method to date (and I've gone through this a number of times before trying it this way) is to use Automatix ... give it a shot, you won't be sorry ... and you can cover a number of different bases at the same time.

Head on over to this thread for more information:  [http://ubuntuforums.org/showthread.php?t=66563&page=1&pp=40](http://ubuntuforums.org/showthread.php?t=66563&page=1&pp=40)

Happy Year End!

---

