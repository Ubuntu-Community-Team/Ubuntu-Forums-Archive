---
title: "Installing Screensaver Plugin on Compiz Fusion"
date: 2007-11-20
forum: Desktop Effects &amp; Customization
---

### Post by Lenois on 2007-11-20
Hi everybody

I want to get the Screensaver plugin for Compiz Fusion. I saw it on Youtube and it looks really cool. However, I am new to Linux (I switched to Ubuntu a week ago) and do not know where to get the screensaver plugin or how to install it. Any help would be appreciated very much.

I'm running Ubuntu 7.10 and the Compiz Fusion that came with it.

Lenois

---

### Post by Mal1024 on 2007-11-20
I would also like to know where to get the plugin.

---

### Post by rattking on 2007-11-20
there is a guide on the compiz-fusion forums on how to compile the missing plugins here
[http://forum.compiz-fusion.org/showthread.php?t=5303](http://forum.compiz-fusion.org/showthread.php?t=5303)

keep in mind that these plugins are not included by default for a reason.. but 3d windows and screensaver seem to be working fine for me

---

### Post by Mattaus on 2007-11-30
Hi,

I followed those instructions for the screensaver plugin and it installed fine. The option to use it appears in the compiz manager, but it won't work for some reason. To test it, instead of waiting 5mins to see if it activated Is et the enable key to super+s, but it does nothing.

Am I missing something here?

Any help would be much appreciated.

---

### Post by Saint Angeles on 2007-11-30
sometimes you have to restart compiz for changes to take effect

---

### Post by Mattaus on 2007-12-01
Ah lol. Yeah I restarted it and its working fine (ish).

I was testing to see if it would activate by itself so Is et the timer to 1minute. Problem was I was mucking around with the default screensaver and had set that to 1 minute as well. So they both went off at the same time. Iw ent to the default one and set it to 20 minutes (blank screen)

Now the screensaver plug in wont activate by itself :confused:

---

### Post by phantom74 on 2008-02-15
i followed that tuttorial on that link and it didnt worked!

can someone help me please (noob)


###Start Log###

dependencies, etc, etc, etc, etc...........

........................................................

Setting up libselinux1-dev (2.0.15-2ubuntu1) ...
Setting up libgnomevfs2-dev (1:2.20.0-0ubuntu3) ...
Setting up libesd0-dev (0.2.38-0ubuntu4) ...
Setting up libgnome2-dev (2.20.0-1ubuntu4) ...
Setting up libbonoboui2-dev (2.20.0-0ubuntu1) ...
Setting up libbz2-dev (1.0.4-0ubuntu2) ...

Setting up libcroco3-dev (0.6.1-1build2) ...
Setting up libdbus-glib-1-dev (0.74-1) ...
Setting up libhal-dev (0.5.9.1-6ubuntu5) ...
Setting up libhal-storage-dev (0.5.9.1-6ubuntu5) ...
Setting up libgnome-keyring-dev (2.20-0ubuntu4) ...
Setting up libjpeg62-dev (6b-14) ...
Setting up libgnomeui-dev (2.20.1.1-0ubuntu1) ...
Setting up libgnome-desktop-dev (1:2.20.1-0ubuntu1) ...
Setting up libgsf-1-dev (1.14.7-0ubuntu1) ...

Setting up librsvg2-dev (2.18.2-1) ...

Setting up libtool (1.5.24-1ubuntu1) ...
Setting up libxslt1-dev (1.1.21-2ubuntu2) ...

Setting up compiz-bcop (0.5.2-0ubuntu1) ...
Processing triggers for libc6 ...
ldconfig deferred processing now taking place
nuno@phantom:~$ mkdir -p  ~/compiz/
nuno@phantom:~$ cd /home/nuno/compiz/
nuno@phantom:~/compiz$ wget -O /tmp/screensaver.tar.gz 'http://gitweb.opencompositing.org/?p=users/pafy/screensaver;a=snapshot;h=6565001eb389fb0d18cfead6030054cc8edc6c5f'
--16:04:07--  [http://gitweb.opencompositing.org/?p=users/pafy/screensaver;a=snapshot;h=6565001eb389fb0d18cfead6030054cc8edc6c5f](http://gitweb.opencompositing.org/?p=users/pafy/screensaver;a=snapshot;h=6565001eb389fb0d18cfead6030054cc8edc6c5f)
           => `/tmp/screensaver.tar.gz'
Resolving gitweb.opencompositing.org... 195.114.19.35
Connecting to gitweb.opencompositing.org|195.114.19.35|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: unspecified [application/x-gzip]

    [   <=>                               ] 14,550        30.31K/s             

16:04:09 (30.21 KB/s) - `/tmp/screensaver.tar.gz' saved [14550]

nuno@phantom:~/compiz$ tar -xf '/tmp/3d.tar.gz' -C ~/compiz/
tar: /tmp/3d.tar.gz: Cannot open: No such file or directory
tar: Error is not recoverable: exiting now



###End Log###

---

### Post by FuturePilot on 2008-02-15
It looks like you downloaded screensaver.tar.gz but you're trying to decompress 3d.tar.gz which doesn't exist.
Try this
```
tar -xf '/tmp/screensaver.tar.gz' -C ~/compiz/
```

---

