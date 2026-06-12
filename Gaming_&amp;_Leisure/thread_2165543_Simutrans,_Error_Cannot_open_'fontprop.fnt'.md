---
title: "Simutrans, Error: Cannot open 'font/prop.fnt'"
date: 2013-08-05
forum: Gaming &amp; Leisure
---

### Post by Keith_Beef on 2013-08-05
I have an odd problem…

I've been playing simutrans installed from Synaptic for a while, but wanted to try a much more recent version. So I downloaded version 102 and used the in-program installer to install some pak files.

But when I try to start the game, I get the messages below.
```

Use work dir /usr/games/
Reading low level config data ...
Preparing display ...
SDL_driver=x11, hw_available=0, video_mem=0, blit_sw=0, bpp=32, bytes=4
Screen Flags: requested=10, actual=10
Error: Cannot open 'font/prop.fnt'
dr_os_open(SDL): SDL realized screen size width=704, height=560 (requested w=704, h=560)Error: No fonts found!
```

I copied the font directory from my previous version, but still get the same result.

```
sudo cp -r ../simutrans102/font/ .
sudo chmod -R a+rx font/
Use work dir /usr/games/
Reading low level config data ...
Preparing display ...
SDL_driver=x11, hw_available=0, video_mem=0, blit_sw=0, bpp=32, bytes=4
Screen Flags: requested=10, actual=10
Error: Cannot open 'font/prop.fnt'
dr_os_open(SDL): SDL realized screen size width=704, height=560 (requested w=704, h=560)Error: No fonts found!

```

Any idea what I'm doing wrong, or why the font directory was not included in the download?

---

### Post by ian-weisser on 2013-08-05
What files do you have in /$game/font ?

For example, here is mine from the packaged version:
```
$ ls -l /usr/share/games/simutrans/font
total 1420
-rw-r--r-- 1 root root  373491 Mar  8  2012 cyr.bdf
-rw-r--r-- 1 root root 1013593 Mar  6  2012 m+10r.bdf
-rw-r--r-- 1 root root    3072 Jun 29  2007 prop.fnt
-rw-r--r-- 1 root root   17934 Mar  6  2012 Prop-Latin1.bdf
-rw-r--r-- 1 root root   19311 Mar  6  2012 Prop-Latin2.bdf
-rw-r--r-- 1 root root    3072 Dec 12  2006 prop-latin2.fnt
-rw-r--r-- 1 root root    3072 Dec 12  2006 ro_font.fnt
```

When I have installed updated versions manually in the past, missing items or directories have not occurred.

---

### Post by Keith_Beef on 2013-08-05
> **ian-weisser said:**
> What files do you have in /$game/font ?

For example, here is mine from the packaged version:
```
$ ls -l /usr/share/games/simutrans/font
total 1420
-rw-r--r-- 1 root root  373491 Mar  8  2012 cyr.bdf
-rw-r--r-- 1 root root 1013593 Mar  6  2012 m+10r.bdf
-rw-r--r-- 1 root root    3072 Jun 29  2007 prop.fnt
-rw-r--r-- 1 root root   17934 Mar  6  2012 Prop-Latin1.bdf
-rw-r--r-- 1 root root   19311 Mar  6  2012 Prop-Latin2.bdf
-rw-r--r-- 1 root root    3072 Dec 12  2006 prop-latin2.fnt
-rw-r--r-- 1 root root    3072 Dec 12  2006 ro_font.fnt
```

When I have installed updated versions manually in the past, missing items or directories have not occurred.

Thanks, Ian.

I already looked in there when I first had the problem&#8230; the whole of the directory /usr/share/games/simutrans/font was missing. This is why I copied it from the previous version (102) and changed the permissions, so that it now contains the following.

```
total 1472
drwxr-xr-x  2 root root    4096 2013-08-05 16:23 .
drwxr-xr-x 12 root root    4096 2013-08-05 16:23 ..
-rwxr-xr-x  1 root root  419701 2013-08-05 16:23 cyr.bdf
-rwxr-xr-x  1 root root 1013381 2013-08-05 16:23 m+10r.bdf
-rwxr-xr-x  1 root root    3072 2013-08-05 16:23 prop.fnt
-rwxr-xr-x  1 root root   17934 2013-08-05 16:23 Prop-Latin1.bdf
-rwxr-xr-x  1 root root   19311 2013-08-05 16:23 Prop-Latin2.bdf
-rwxr-xr-x  1 root root    3072 2013-08-05 16:23 prop-latin2.fnt
-rwxr-xr-x  1 root root    3072 2013-08-05 16:23 ro_font.fnt
```

So there's a prop.fnt there, in the font directory. The error message states "Cannot open 'font/prop.fnt'", and not "Cannot find  'font/prop.fnt'".

I also tried starting with the -log option; this generates a logfile in ~/simutrans, but this just contains two lines.

```

Simutrans version 112.3 from May 19 2013 r6520
Preparing display ...

```

Simtrans seems to find the file but cannot open it, but does not tell me why.

---

### Post by ian-weisser on 2013-08-05
That description smells like a permissions issue.
Packaged Simutrans installs to /usr, and all the files are owned by root. Manually-installed Simutrans is typically owned by a user, and all the files should be owned by that user. Yours are owned by root instead of user.

Aside, I see is that your fonts are all executable. Fonts usually don't need that.

---

### Post by Keith_Beef on 2013-08-07
> **ian-weisser said:**
> That description smells like a permissions issue.
Packaged Simutrans installs to /usr, and all the files are owned by root. Manually-installed Simutrans is typically owned by a user, and all the files should be owned by that user. Yours are owned by root instead of user.

Aside, I see is that your fonts are all executable. Fonts usually don't need that.

I've tried several different command line options, thinking that the executable needed more help finding the right files, but still to no avail.

For example:
```
simutrans -use_dir /usr/share/games/simutrans/ -log -debug 5
```

gives me this in the log file```


Simutrans version 112.3 from May 19 2013 r6520
Message: simmain::main():	Version: 112.3  Date: May 19 2013
Message: Debuglevel:	5
Message: program_dir:	/usr/games/
Message: home_dir:	/home/keith_beef/simutrans/
Message: locale:	en
Message: obj_reader_t::read_file():	filename='skin/ground.Outside.pak'
ERROR: obj_reader_t::read_file():	reading 'skin/ground.Outside.pak' failed!
For help with this error or to file a bug report please see the Simutrans forum:
http://forum.simutrans.com
Warning: obj_reader_t::load():	ground.Outside.pak not found, cannot guess tile size! (driving on left will not work!)
Message: obj_reader_t::load():	reading from 'skin/'
Message: obj_reader_t::read_file():	filename='skin/ground.Outside.pak'
ERROR: obj_reader_t::read_file():	reading 'skin/ground.Outside.pak' failed!
For help with this error or to file a bug report please see the Simutrans forum:
http://forum.simutrans.com
Warning: obj_reader_t::load():	ground.Outside.pak not found, cannot guess tile size! (driving on left will not work!)
Message: obj_reader_t::load():	reading from 'skin/'
Preparing display ...
Message: simmain:	simgraph_init disp_width=704, disp_height=560, fullscreen=0
```

Executing with sudo changes nothing, so I don't think that there is a problem with permissions&#8230;

I cannot find a file named ground.Outside.pak in the skin directory, though, so maybe this is the root cause of the problem.
```
$ ls -al /usr/share/games/simutrans/skin/
total 36
drwxr-xr-x  2 root root  4096 2013-08-05 12:07 .
drwxr-xr-x 12 root root  4096 2013-08-05 16:23 ..
-rw-rw-r--  1 root root 26185 2012-02-28 23:02 menu.WindowSkin.pak
```

---

### Post by ian-weisser on 2013-08-07
Yours is like mine.

```
$ ls -l /usr/share/games/simutrans/skin
total 32
-rw-r--r-- 1 root root 29853 May 16 04:23 menu.WindowSkin.pak
```

Hmm. How, exactly, did you install this version manually?
When I have installed manually, I had a few permissions issues. But nothing like you are suffering.

---

