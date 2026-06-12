---
title: "rhythmbox/gstreamer and musepack (mpc)"
date: 2005-03-14
forum: Desktop Environments
---

### Post by burlap on 2005-03-14
I am lost. It seems that gstreamer should support mpc (musepack) audio, but I can't load mpc files into rhythmbox. 

gst-inspect shows no signs of mpc either. 

Gstreamer web site is quite, hmm, useless (unless I would like to write plugins myself). 

So, my question is: is mpc supported with gstreamer? Or more precisely: is mpc supported with gstreamer in Ubuntu Warty? 

If not: is it possible to use mpc with rhythmbox at all (using some external libraries)? I've just come to like rhythmbox (muine looks tempting but I want to start my adventures in mono only when Hoary goes stable) and what a nasty surprise... 

And BTW: is there any nice method to convert mpc into mp3? Or do I have to convert mpc to wav and wav to mp3? I need mp3 for my stereo.

---

### Post by kassetra on 2005-03-14
[QUOTE=burlap] Or more precisely: is mpc supported with gstreamer in Ubuntu Warty? 

If not: is it possible to use mpc with rhythmbox at all (using some external libraries)? I've just come to like rhythmbox (muine looks tempting but I want to start my adventures in mono only when Hoary goes stable) and what a nasty surprise... 

And BTW: is there any nice method to convert mpc into mp3? Or do I have to convert mpc to wav and wav to mp3? I need mp3 for my stereo.[/QUOTE]

Let's break this down a bit.  mpc will work in ubuntu, but you need a few things to play those files.  (the gst-musepack library is in the cvs version of gst-plugins)

1. You need a player capable of playing musepack files, there are two I know work well, xmms and beep-media-player (bmp) ...  I suggest you install beep-media-player.  Go to Computer->System Configuration->Synaptic Package Manager and search for beep-media-player and install it (make sure you also install the -dev).  If you don't know how to do that, let me know.
2. You'll also need a library and a plugin for the player.
Get the [plugin here]("http://www.saunalahti.fi/grimmel/musepack.net-files/linux/plugins/bmp-musepack-1.1.2.tar.bz2").
Get the [library here]("http://www.saunalahti.fi/grimmel/musepack.net-files/source/libmusepack-1.1.tar.bz2").
You'll need to install both of these as well.  If you don't know how to do that, I can help as well.

As for the second bit, yes, it is very possible to convert from mpc to mp3... but remember you're going from lossy to lossy format, so there may be some glitches in the process.

You have to use mppdec and then something like lameenc... do you know how to do that?

---

### Post by kassetra on 2005-03-14
Oh... there is also somewhat of a shortcut installing mpc support - 

If you install beep-media-player from the backports repositories, and then also install bmp-extra-plugins from the backports extras, mpc is built in.  :)

---

### Post by burlap on 2005-03-15
> 1. You need a player capable of playing musepack files, there are two I know work well, xmms and beep-media-player (bmp) ...  
I know that. I've used both xmms and bmp and I know how to install plugins and all. I just wondered if it was possible with rhythmbox. (I am also trying to solve this issue via gstreamer bugzilla, #170368. I have posted here to make sure that for example Ubuntu Warty packages are not the reason. And rhythmbox, while I was uploading mpc files reported an error and asked to file a bug.).
> If you install beep-media-player from the backports repositories, and then also install bmp-extra-plugins from the backports extras, mpc is built in. 
I always look in the repositories first before I start compiling. I haven't seen backported bmp there - but there is solution for everything: I don't use "staging" backports/extras. Of course, when I really need it, I will use it anyway. 
> As for the second bit, yes, it is very possible to convert from mpc to mp3... but remember you're going from lossy to lossy format, so there may be some glitches in the process.
I know that also. It's just my stereo that plays mp3 only... And, errrr, I happen to have only mpc, my cd is, umm, lost somewhere.  ;-) 
> You have to use mppdec and then something like lameenc... do you know how to do that?
I don't know the exact options, but that's not the point. As there are man pages it's not really necessary to bother forums (I can alwasy try decoder -someoption | encoder -someoption). I am lazy though and I thought that maybe there was something that could do it automagically (preserving tags for example). 

Thanks for the repositories and cvs info anyway.

---

### Post by WMCoolmon on 2005-04-07
I've tried installing the plugin/library via source compilation, and it hasn't worked. The plugin seems to compile and install fine, it shows up in the same directory with all the other input plugins, it just doesn't show up in beep-media-player. I even tried stripping it (libmpc.so was stripped, the rest of the plugins weren't, the only difference according to file)

I tried the xmms plugin as well; same thing, although now it gives me errors like:
> src/Makefile.am:3: Libtool library used but `LIBTOOL' is undefined
src/Makefile.am:3:
src/Makefile.am:3: The usual way to define `LIBTOOL' is to add `AC_PROG_LIBTOOL'src/Makefile.am:3: to `configure.in' and run `aclocal' and `autoconf' again.
make: *** [Makefile.in] Error 1
whenever I try to do anything with make. :-/

---

