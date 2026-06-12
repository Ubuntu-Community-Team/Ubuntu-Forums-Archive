---
title: "Listening to BBC radios with Warthy ?"
date: 2005-01-11
forum: General Help
---

### Post by francois.schnell on 2005-01-11
Hello  :) 

I want to listen to BBC radios with my new beloved Ubuntu Warthy ...

=>

I've  installed Real Player following this:
[http://ubuntuguide.org/#realplayer](http://ubuntuguide.org/#realplayer)
and it works fine.

But,
If i want to listen to BBC radios with ubuntu-firefox:
[http://www.bbc.co.uk/radio/aod/radio1.shtml?listen](http://www.bbc.co.uk/radio/aod/radio1.shtml?listen)
I have the message: "could not find an appropriate hxplay or realplay in the system path to use as an embeded player".

But,
```

If i do about:plugins in firefox I see :

Helix DNA Plugin: RealPlayer G2 Plug-In Compatible

    File name: nphelix.so
    Helix DNA Plugin: RealPlayer G2 Plug-In Compatible version 0.4.0.404 built with gcc 3.2.0 on Dec 14 2004

MIME Type 	Description 	Suffixes 	Enabled
audio/x-pn-realaudio-plugin 	RealPlayer Plugin Metafile 	rpm 	Yes
```

```


and if i do  ls -al /usr/lib/mozilla/plugins  I have :

total 2080
drwxr-xr-x    2 root     root         4096 2005-01-09 23:12 .
drwxr-xr-x   11 root     root         4096 2005-01-09 23:12 ..
-rw-r--r--    1 root     root          856 2004-05-28 14:28 flashplayer.xpt
-rw-r--r--    1 root     root      2092960 2004-05-28 14:28 libflashplayer.so
lrwxrwxrwx    1 root     root           58 2005-01-06 10:11 libjavaplugin_oji.so -> /usr/java/jre1.5.0_01/plugin/i386/ns7/libjavaplugin_oji.so
-rw-r--r--    1 root     root        19376 2004-09-24 10:15 libnullplugin.so
lrwxrwxrwx    1 root     root           34 2005-01-05 18:35 nphelix.so -> /opt/RealPlayer/mozilla/nphelix.so
lrwxrwxrwx    1 root     root           35 2005-01-05 18:35 nphelix.xpt -> /opt/RealPlayer/mozilla/nphelix.xpt
lrwxrwxrwx    1 root     root           43 2005-01-05 15:19 nppdf.so -> ../../Acrobat5/Browsers/intellinux/nppdf.so
```

What's wrong with me ?  help ...

---

### Post by godvalve on 2005-12-17
I just had that this same problem...

However, the error didn't make any sense.  I installed the player and went to the radio1 site. The player was streaming but I didn't hear any sound. I'm using alsa and so I chased down some info on how to get realplayer to use alsa. After following the instructions, I went back to radio1 and got this error (and the player wasn't steaming anymore). So, I decided that I must have done something wrong when I edited the realplayer config file (realplay). I also did a quick google and found a post that said that the problem can be caused by incorrect symlinks.  Just to be on the safe side I deleted the whole realplayer directory and redid the install. Then I altered the realplay config file as per this guide: [HOWTO - Get RealPlayer to use ALSA instead of OSS]("http://www.ubuntuforums.org/showthread.php?t=44753&highlight=HOWTO+RealPlayer+ALSA+OSS"). This fixed everything.

Hope this helps someone.  ;)

---

