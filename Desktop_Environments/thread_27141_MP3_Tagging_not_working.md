---
title: "MP3 Tagging not working"
date: 2005-04-15
forum: Desktop Environments
---

### Post by getaceres on 2005-04-15
I know libtunepimp-bin has been compiled without mp3 so I can't tag my mp3 files (thanks to Ubuntu policies, I gess) so I've tried to compile it myself with apt-build but it says it can't find libtunepimp-bin ¿What repositories do I have to add to have all the sources from Ubuntu? I added 
deb-src [http://archives.ubuntu.org/ubuntu](http://archives.ubuntu.org/ubuntu) hoary main restricted universe multiverse
Does anyone have the right libtunepimb-bin package?
Thanks.

---

### Post by Buffalo Soldier on 2005-04-15
Checked using synaptic. I've found libtunepimp-bin (version 0.3.0-2ubuntu5). The repositories that I have enabled are main, restricted, universe, and multiverse.

Out of topic question. What made you decide not to use **easytag**?

---

### Post by getaceres on 2005-04-15
I'm using amarok to tag the mp3 files but I'll try easytag. I don't mind using GTK apps if they are better than their QT counterpart.
The problem is not that libtunepimp-bin isn't there. It is, but it's compiled without mp3 support so you can tag ogg files but not mp3 files. The solution I've found searching in the forums is to recompile libtunepimp-bin using apt-build but I get some errors when I put 'sudo apt-get --reinstall libtunepimp-bin' saying it can't find libtunepimp-bin.

---

### Post by Alexander Kirillov on 2005-04-15
[QUOTE=Buffalo Soldier]
Out of topic question. What made you decide not to use **easytag**?[/QUOTE]

Easy tag has horrendous interface design (just look at their preferences), but one can get used to it. What really makes me mad is that the support for MP3 tags in any encoding but Latin-1  is completely broken.

---

### Post by Psquared on 2005-04-15
I don't know about anybody else, but I get errors with EasyTag. If I change the tags on one file it has to go through every single mp3 before it will close. I had to stop using it for that reason. (Oh, I am using Warty)

---

### Post by getaceres on 2005-04-15
[QUOTE=Buffalo Soldier]
Out of topic question. What made you decide not to use **easytag**?[/QUOTE]

I've tried EasyTagger and is not what I was looking for. It does not have the option to download tags from MusicBrainz. Is not that I can't edit tags with Amarok, the problem is that Musicbrainz is not working with mp3 files.

Anyway. Finally I have managed to download libtunepimp and compile it with mp3 support. I know the mp3 issue Ubuntu has but, why not to put a version of the affected libraries in Universe compiled with mp3 support so anyone not worried about that issue can download it?

---

### Post by ceti on 2005-04-15
Easytag sucks.
Try tagtool. Clean interface, no preferences hell, bash renames & tags.
 
ceti

---

