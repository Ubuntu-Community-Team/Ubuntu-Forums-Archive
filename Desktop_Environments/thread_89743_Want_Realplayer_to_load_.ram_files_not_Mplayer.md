---
title: "Want Realplayer to load .ram files not Mplayer"
date: 2005-11-13
forum: Desktop Environments
---

### Post by Darrin on 2005-11-13
Im trying to launch some of [these audio files.]("http://bteministries.org/freebiblestudies.htm#Acts") Firefox launches them with mplayer. I would like realplayer to load these particular file types. How do I change this.
Thank you.

---

### Post by Darrin on 2005-11-13
Looks like I had to do what I did once before. Uninstall firefox and reinstall it. [My previous post]("http://ubuntuforums.org/showthread.php?t=86971")
Dont know of an easier way.

---

### Post by bionnaki on 2005-11-13
edit>preferences>downloads>download actions>"view and edit actions"
and change the default application for .ram & .ra & other real media associations.

---

### Post by Darrin on 2005-11-13
[QUOTE=bionnaki]edit>preferences>downloads>download actions>"view and edit actions"
and change the default application for .ram & .ra & other real media associations.[/QUOTE]
Are these steps to perform in Firefox?
I have Edit>Preferences>Downloads but no download actions.

---

### Post by dcstar on 2005-11-14
[QUOTE=Darrin]Im trying to launch some of [these audio files.]("http://bteministries.org/freebiblestudies.htm#Acts") Firefox launches them with mplayer. I would like realplayer to load these particular file types. How do I change this.
Thank you.[/QUOTE]

There is a realplayer 10 deb package available from this repository:

[ftp://ftp.nerim.net/debian-marillat/](ftp://ftp.nerim.net/debian-marillat/) sarge main

It may link up the proper plug-in stuff when installed (I have a slightly different version installed which fixed up all my Firefox issues in this area).

---

### Post by cjazz on 2005-11-14
I had a similar problem with Mplayer hijacking Real audio files, despite the fact that the Real Player plugin was installed. This happened in spite of the fact that Firefox's Downloads tab in Preferences showed the Real plugin as automatically associated with .ram files.

I managed to bring Real Player back into the mix by installing the MediaPlayerConnectivity extension for Firefox.

---

### Post by shof2k on 2005-11-14
A more brutal way is to look in /usr/lib/mozilla-firefox/plugins or ~/.mozilla/plugins and delete the mplayer plugin files.  This will make firefox prompt you again so you can choose realplayer.

You may need to link the files nphelix.so and nphexli.xpt to this folder too, but that could be my box being funny.

Hope that helps

---

