---
title: "Errors after enabling universe and multiverse repositories"
date: 2005-12-23
forum: General Help
---

### Post by nami on 2005-12-23
Hi

I wanted to install some codecs so I could play my mp3 tracks in rhythmbox.  So I started to follow the instructions on the following page: [http://help.ubuntu.com/starterguide/C/faqguide-all.html#sect-music-and-movies](http://help.ubuntu.com/starterguide/C/faqguide-all.html#sect-music-and-movies)

It said that I first need to make sure the universe and multiverse repositories are enabled.  So I followed the following instructions: [http://help.ubuntu.com/starterguide/C/faqguide-all.html#addinguniverse](http://help.ubuntu.com/starterguide/C/faqguide-all.html#addinguniverse)

I did exactly as it was written and now, each time I go into the Synaptic Package Manager, I get the following error message:

Click to enlarge.
[[IMG]http://img463.imageshack.us/img463/9489/screenshot14mx.th.png[/IMG]](http://img463.imageshack.us/img463/9489/screenshot14mx.png)

Anyone know what these errors mean and why I'm getting them?

nami

---

### Post by schucki.be on 2005-12-23
I've got the same problem.
Thought i was stupid:p 
I am using the NL-archives, but it seems impossible to load the multiverse repos.

Tried the BE-archs to, but same result.

Because the multiverse repos won't load, many of the instructions won't work...

---

### Post by schucki.be on 2005-12-23
Hey Nami,
Found possible solution.
A posting from 65 Mustang; apt-get help

sudo -s -H
apt-get update

This seems to work for me...:razz: 

Maybe for u 2 ?

Grtz,

schucki.be

---

### Post by nami on 2005-12-24
Hi schucki.be,

That worked perfectly!  Thanks very much.

nami.

---

