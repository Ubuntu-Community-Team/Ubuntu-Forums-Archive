---
title: "RealPlayer prob"
date: 2005-03-30
forum: Desktop Environments
---

### Post by vaskark on 2005-03-30
I installed RealPlayer 10 Gold from their website. RealPlayer opens fine for me (after disabling ESD sound daemon -- I found that out from other posts) but when I load a site that uses real video the plugin doesn't show up, just a message saying I need RealPlayer (duh). In Firefox I looked in 'about:plugins' and found this:

 ```
Helix DNA Plugin: RealPlayer G2 Plug-In Compatible
File name: nphelix.so Helix DNA Plugin: RealPlayer G2 Plug-In Compatible version 0.4.0.544 built with gcc 3.2.0 on Feb 23 2005

MIME Type Description Suffixes Enabled
audio/x-pn-realaudio-plugin RealPlayer Plugin Metafile rpm Yes
```       

Shouldn't the "ram" format be listed as well? I then did 'ls -l' in /usr/lib/mozilla-firefox/plugins to check that the plugins were configured properly:

 ```
lrwxrwxrwx  1 root root 34 2005-03-30 21:14 nphelix.so -> /opt/RealPlayer/mozilla/nphelix.so
lrwxrwxrwx  1 root root 35 2005-03-30 21:14 nphelix.xpt -> /opt/RealPlayer/mozilla/nphelix.xpt
``` 

Am I missing anything here? Can someone who has RealPlayer successfully working do 'ls -l' in their firefox plugins directory to see if I'm missing some symlinks?

Thanks.

---

### Post by dukeinlondon on 2005-03-31
[www.bbc.co.uk](www.bbc.co.uk) videos don't work here either. I've got the same files in the plugins directory of firefox. I've also tried the plugin in konkeror and what I get is a freeze of konkeror..... (kde 3.4)

---

### Post by shof2k on 2005-04-05
Try the following thread
[http://ubuntuforums.org/showthread.php?t=23840](http://ubuntuforums.org/showthread.php?t=23840)

Essentially:
1) Edit  /etc/esound/esd.config and set auto-span=1
2) Remove the SWF* prefixed files from /opt/Realplayer/Plugin (or wherever you installed to)
3) linking the nphelix plugins to firefox.  (I prefer doing this in  ~/.mozilla/plugins)
4) Rebooting

Also Realplayer 10.2 seemed to for me instead of 10.3.

---

### Post by M.R on 2005-04-07
[QUOTE=shof2] 3) linking the nphelix plugins to firefox.  (I prefer doing this in  ~/.mozilla/plugins)[/QUOTE]

How do you do that?

MR

---

### Post by skoal on 2005-04-07
I followed [this](http://www.ubuntuguide.org/#realplayer) guide with no problems.  The BBC UK videos play fine too.

It should set up the firefox plugins as well if you follow those instructions.  Those plugins are located in:

/usr/lib/mozilla/plugins

```
skoal@morpheus:~ $ ls -al /usr/lib/mozilla/plugins/
total 196
drwxr-xr-x  2 root root    152 2005-04-07 00:35 .
drwxr-xr-x  4 root root    136 2005-04-07 00:13 ..
-rw-r--r--  1 root root 199840 2005-04-04 09:42 mplayerplug-in.so
lrwxrwxrwx  1 root root     34 2005-04-07 00:35 nphelix.so -> /opt/realplayer/mozilla/nphelix.so
lrwxrwxrwx  1 root root     35 2005-04-07 00:35 nphelix.xpt -> /opt/realplayer/mozilla/nphelix.xpt
```

---

