---
title: "Banshee 0.9.9"
date: 2005-11-01
forum: Deferred/Invalid Requests
---

### Post by vassie on 2005-11-01
Any chance of this?

[http://banshee-project.org/index.php/Main_Page](http://banshee-project.org/index.php/Main_Page)

Here is the change log from the version in Breezy, as you can see, there is some pretty nice changes

[http://mail.gnome.org/archives/banshee-list/2005-October/msg00020.html](http://mail.gnome.org/archives/banshee-list/2005-October/msg00020.html)

Thanks

Ben

---

### Post by vassie on 2005-11-03
0.9.10 is out now, so that would be nice instead

Thanks

Ben

---

### Post by Technoviking on 2005-11-03
Looks like it requires the new version of mono:(, something more than I would want to do.

Mike

---

### Post by poofyhairguy on 2005-11-03
[QUOTE=Mike Basinger]Looks like it requires the new version of mono:(, something more than I would want to do.

Mike[/QUOTE]


I cry.

---

### Post by pizzach on 2005-11-06
No it actually doesn't  Appearances are decieving.  I read that it'll run on the version of mono included with breezy.  But it does need to be compiling with some newer mono components, which seem to be included with the banshee src and does it itself if you type ./configure --with-internal-mcs.  I actually installed the newer of mono so I can't say I've tried it though.

---

### Post by vassie on 2005-11-08
I have just installed Banshee 0.9.10 from source on Breezy, and it is a HUGE improvement over 0.9.7, can someone look into backporting this, as it was a right pain in the a**e to compile.

Thanks

Ben

(PS, I have taken some screenshots of 0.9.10, I'll upload them to Flickr when I get to work)

(PPS, I am also going to write a procedure on how I installed it)

---

### Post by vassie on 2005-11-09
Hello
If anyones interested, I have created my own deb's of banshee.0.9.10, you can find them [here]("http://www.benvassie.net/2005/11/08/how-to-compile-banshee-0910-under-breezy/").
Ben

---

### Post by jdong on 2005-11-09
Unfortunately with this level of modification, Banshee is not up for backporting. However, since Mono backports are planned by Ubuntu mono developers, this situation may change in the future.

---

