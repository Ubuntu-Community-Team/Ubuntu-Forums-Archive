---
title: "Savage problem"
date: 2006-09-08
forum: Gaming &amp; Leisure
---

### Post by medeshago on 2006-09-08
I followed these instructions to install savage:
[http://www.christoph-zauner.de/savage/mediawiki/index.php/Installation](http://www.christoph-zauner.de/savage/mediawiki/index.php/Installation)
but when i tried to run it, i get these error:
./silverback.bin: /usr/lib/libGL.so.1: no version information available (required by ./silverback.bin)
System_Init()


i need help!

---

### Post by Perfect Storm on 2006-09-08
Have you installed 3D acc. driver for your graphic card?

---

### Post by medeshago on 2006-09-08
yes. i can play enemy territory.

---

### Post by Casey on 2006-09-09
Instead of the SEP that is supplied there, try this one instead (much newer):
[http://www.notforidiots.com/forum/viewtopic.php?t=1200](http://www.notforidiots.com/forum/viewtopic.php?t=1200)

---

### Post by jdunn on 2006-09-09
Casey, can you plz re-post directions on how to install?  I pretty much know what I'm doing and I do have glx drivers installed.  However, there are at least two different sets of directions and none of them seem to work.  I tried this:  

[http://www.notforidiots.com/forum/viewtopic.php?t=1200](http://www.notforidiots.com/forum/viewtopic.php?t=1200) 

and I tried it with the updated SEP3T.  I also tried this with no luck: 

[http://www.ubuntuforums.org/showthread.php?t=249916](http://www.ubuntuforums.org/showthread.php?t=249916)

There are alot of updates to install before this game can be run and its easy to skip an update.

---

### Post by Casey on 2006-09-09
The steps I took when I installed it were:

Install savage (run ./savage_linux.sh)

Install patch (run ./savage_2.00c-english.update.run)

download SEP3T
[http://www.notforidiots.com/autoupdater/SEP-3T.tar.gz](http://www.notforidiots.com/autoupdater/SEP-3T.tar.gz)

Extract it into it's own folder.
Copy all the files from that folder into the base savage folder (overwrite when prompted)

enter the savage directory in a terminal type:
nano -w savage

Look for this line:
LD_LIBRARY_PATH=libs:$LD_LIBRARY_PATH ./savage.bin (INSTALL LOCATION)

Replace savage.bin with silverback.bin (skips the s2games auto-updater -- which they no longer use anyway, and might avoid some problems that way)

ctrl-w to save
ctrl-x to exit

--

Hope this helps!

---

### Post by medeshago on 2006-09-10
i did everything you said and now it enters, but i get all messed up graphics, i can't see anything, it's like a repetitive patern of... i don't know... something weird. I get audio.

---

### Post by Casey on 2006-09-10
> **medeshago said:**
> i did everything you said and now it enters, but i get all messed up graphics, i can't see anything, it's like a repetitive patern of... i don't know... something weird. I get audio.

I just posted a detailed installation thread here:
[http://www.ubuntuforums.org/showthread.php?p=1482725#post1482725]("http://www.ubuntuforums.org/showthread.php?p=1482725#post1482725")

Hope this helps!

---

