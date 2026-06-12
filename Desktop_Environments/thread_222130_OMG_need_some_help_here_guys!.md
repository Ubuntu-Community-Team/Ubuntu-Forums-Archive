---
title: "OMG need some help here guys!"
date: 2006-07-24
forum: Desktop Environments
---

### Post by Luthy on 2006-07-24
I cant seem to create audio cd's w/ Gnomebaker or KBB3 or anything. All files are in MP3 format. Anyway to make audio cd's with them? Says i need a pluggin for all my Burners i use (aka GnomeBaker KBB3 ect.) where do i get them? ive looked Synaptic but im clueless. HELP PLEASE!

---

### Post by Ziox on 2006-07-24
first off, can you play those mp3? Because Ubuntu doesn't have mp3 support out of the box (not open source).  Now have you tried to create cd with serpentine? I've heard that it is very simple...

EDIT: also make sure that you have cdrecord installed, which i assume is installed

---

### Post by endfx on 2006-07-24
Hi there,

First of all, the next time you post a message in the help forum, can you please use a better Title/subject then "HELP"? Thanks.

Now Ubuntu doesn't come with a lot of mp3 capabilities (worried about legal issues) so to answer you question follow this link:

[http://ubuntuguide.org/wiki/Dapper#How_to_burn_Audio_CD_from_MP3_.28GnomeBaker.29](http://ubuntuguide.org/wiki/Dapper#How_to_burn_Audio_CD_from_MP3_.28GnomeBaker.29)

That link is literally a step by step guide on how to do what you want.

The only thing is, at the top of the page, there is a "sources" list. You will have to use that instead of your current sources list.
The sources list is found in /etc/apt/sources.lst. All it is, is a list of places of where to download files/applications (called a repository)

Anyways, give that guide a shot, and let me know if you have any more problems :)

---

### Post by Ziox on 2006-07-24
> **endfx said:**
> 
The sources list is found in /etc/apt/sources.lst. All it is, is a list of places of where to download files/applications (called a repository)

Anyways, give that guide a shot, and let me know if you have any more problems :)

a minor mistake, but that makes all the difference.  The file you need to edit is /etc/apt/sources.list.  I know it's only one letter, and everyone makes that simple mistake:p , but it won't work unless its absolutely exact.

---

### Post by endfx on 2006-07-24
Right, /etc/apt/sources.list.

(I was debugging some grub issues this morning, so I have the filename "menu.lst" in my head")

---

### Post by ajgreeny on 2006-07-24
K3b needs the package libk3b2-mp3 to work and you also need the other codecs to play mp3 files.  There are plenty of places in the forum with info on those so do a search and I'm sure you'll find them.

---

### Post by Luthy on 2006-07-24
Thank you so much guys. it now works. im so srry bout the topic thread i made! Thanks boy do i feel like the low woman on the totem pole lol. :-)

---

