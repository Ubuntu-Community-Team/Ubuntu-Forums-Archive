---
title: "Problem Installing Screensaver Plugin in Compiz"
date: 2010-04-16
forum: Desktop Environments
---

### Post by Xorlathor on 2010-04-16
I'm following the instructions from here:

[http://ubuntuforums.org/showthread.php?t=602003](http://ubuntuforums.org/showthread.php?t=602003)

I enter the following command into the terminal:

```
sudo apt-get install compiz-fusion-bcop compiz-dev build-essential libxcomposite-dev libpng12-dev libsm-dev libxrandr-dev libxdamage-dev libxinerama-dev libstartup-notification0-dev libgconf2-dev libgl1-mesa-dev libglu1-mesa-dev libmetacity-dev librsvg2-dev libdbus-1-dev libdbus-glib-1-dev libgnome-desktop-dev libgnome-window-settings-dev gitweb curl autoconf automake automake1.9 libtool intltool libxslt1-dev xsltproc x11proto-scrnsaver-dev libxss-dev
```

Works fine - installs everything without a problem.

I enter the next command:

```
wget -O /tmp/screensaver.tar.gz 'http://gitweb.opencompositing.org/?p=users/pafy/screensaver;a=snapshot;h=6565001eb389fb0d18cfead6030054cc8edc6c5f' mkdir -p  ~/compiz/
```

It only works partially, outputting this:

robert@robert-laptop:~$ wget -O /tmp/screensaver.tar.gz 'http://gitweb.opencompositing.org/?p=users/pafy/screensaver;a=snapshot;h=6565001eb389fb0d18cfead6030054cc8edc6c5f' mkdir -p  ~/compiz/
[B]WARNING: combining -O with -r or -p will mean that all downloaded content
will be placed in the single file you specified.[/B]

--2010-04-16 14:43:11--  [http://gitweb.opencompositing.org/?p=users/pafy/screensaver;a=snapshot;h=6565001eb389fb0d18cfead6030054cc8edc6c5f](http://gitweb.opencompositing.org/?p=users/pafy/screensaver;a=snapshot;h=6565001eb389fb0d18cfead6030054cc8edc6c5f)
Resolving gitweb.opencompositing.org... 195.114.19.35
Connecting to gitweb.opencompositing.org|195.114.19.35|:80... connected.
HTTP request sent, awaiting response... 301 Moved Permanently
Location: [http://gitweb.compiz.org/?p=users/pafy/screensaver;a=snapshot;h=6565001eb389fb0d18cfead6030054cc8edc6c5f](http://gitweb.compiz.org/?p=users/pafy/screensaver;a=snapshot;h=6565001eb389fb0d18cfead6030054cc8edc6c5f) [following]
--2010-04-16 14:43:11--  [http://gitweb.compiz.org/?p=users/pafy/screensaver;a=snapshot;h=6565001eb389fb0d18cfead6030054cc8edc6c5f](http://gitweb.compiz.org/?p=users/pafy/screensaver;a=snapshot;h=6565001eb389fb0d18cfead6030054cc8edc6c5f)
Resolving gitweb.compiz.org... 195.114.19.35
Reusing existing connection to gitweb.opencompositing.org:80.
HTTP request sent, awaiting response... 200 OK
Length: unspecified [application/x-gzip]
Saving to: `/tmp/screensaver.tar.gz'

    [  <=>                                  ] 14,550      39.9K/s   in 0.4s    

2010-04-16 14:43:12 (39.9 KB/s) - `/tmp/screensaver.tar.gz' saved [14550]

[B]--2010-04-16 14:43:12--  [http://mkdir/](http://mkdir/)
Resolving mkdir... failed: Name or service not known.
wget: unable to resolve host address `mkdir'
/home/robert/compiz/: Scheme missing.[/B]
FINISHED --2010-04-16 14:43:12--
Downloaded: 1 files, 14K in 0.4s (39.9 KB/s)



Why is it apparently trying to download something from [http://mkdir/](http://mkdir/) when that's a command? What did I do wrong? 

Help would be greatly appreciated!

---

### Post by immerohnegott on 2010-04-16
you seem to be putting that whole thing in as one line, which means wget is taking mkdir as an argument, so it tries to download from [http://mkdir](http://mkdir).

put an && (double ampersand) between the last wget argument and the mkdir command. This tells the console to break after wget and run the new command.

---

### Post by immerohnegott on 2010-04-16
```
wget -O /tmp/screensaver.tar.gz 'http://gitweb.opencompositing.org/?p=users/pafy/screensaver;a=snapshot;h=6565001eb389fb0d18cfead6030054cc8edc6c5f' && mkdir -p  ~/compiz/
```

like so

---

### Post by Xorlathor on 2010-04-16
Never mind, I solved this myself by following the instructions here: [http://wiki.compiz.org/Install/PluginsFromGit](http://wiki.compiz.org/Install/PluginsFromGit) 

Now I need to restart compiz and everything should work.

---

### Post by Xorlathor on 2010-04-16
Okay now I need to find out how to make a background while the apps are spinning around instead of blackness - how can I do this?

---

### Post by Xorlathor on 2010-04-16
Does anybody know how to keep a background image while the screensaver is activated? Right now it's just blackness.

---

### Post by soad6 on 2010-11-28
Hey I followed what you said and got one question where is this plugin at??

---

