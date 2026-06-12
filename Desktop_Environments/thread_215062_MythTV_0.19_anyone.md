---
title: "MythTV 0.19 anyone?"
date: 2006-07-13
forum: Desktop Environments
---

### Post by manoova on 2006-07-13
I've been hacking away at MythTV for a while now. It seems that the easiest way to get it installed is to install Ubuntu 6.06 + MySQL 4 (not v5) + apache2 + PHP5 + MythTV 0.18 from universe.

Is anyone working on packaging v0.19 for Ubuntu 6.06 with MySQL 5? I'm aware that there are some unofficial repositories available and I have used them but I find them less than perfect to be honest.

Even if a 0.19 package is only a good few months away it would be great to know if anyone is working on it.

---

### Post by viciouslime on 2006-07-13
Yeh I would also like to know about this. here in the UK 0.19 is really necessary for those of us withdigital cards because it supports getting the tv guide info from the card so we dont have to spend hours setting up xmltv.

---

### Post by StalfoS on 2006-07-14
I compiled it from source, and it works great on my amd64.  I used checkinstall to install it with dpkg.

---

### Post by xinix on 2006-07-14
There are a few mythtv 0.19 package repos on the web I've had ok luck with them but I'm considering compiling my own.  after all what I understand is that video apps are best when you roll your own.

Mythtv 0.19 repos for those inerested:

deb [http://home.eng.iastate.edu/~superm1](http://home.eng.iastate.edu/~superm1) dapper main
deb-src [http://home.eng.iastate.edu/~superm1](http://home.eng.iastate.edu/~superm1) dapper main
or
deb [http://knm.org/mythdebs/](http://knm.org/mythdebs/) binary/
deb-src [http://knm.org/mythdebs/](http://knm.org/mythdebs/) source/


I haven't gotten some of the plugins to install.  I really haven't tried though.

---

### Post by sebz2005 on 2006-07-14
I tryed but it said that it cant find the front-ends for it.

---

### Post by manoova on 2006-07-14
It would be great if someone does take this on as a project to package MythTV 0.19 for the Ubuntu repositories. I believe that MythTV is an excellent advert for both Ubuntu and Linux in general.

It literally is a TV advert for Open Source! Having it running in in the living room/lounge is a great way to show of Linux's capabilities to those who are unaware it even exists.

---

### Post by Grey on 2006-07-14
Yeah, I'm running 0.18 on amd64 with some modification.  

I fixed the ati_remote kernel module that's broken in dapper by changing two lines of code, and recompiling...

And I enabled transcode support in mythdvd, and aac in mythmusic by changing the compile options, and recompiling the debs from the deb-src.

But I've been attempting to keep the system fairly clean, so I haven't done any extensive changes beyond that... although I do like some of the features in 0.19.  Official debs in Edgy would be fantastic.

If anyone would like my kernel, or my myth plugins debs, send me a PM with your email address, and I'll see if I can send them over.  ATI Remote Wonder works fine on this system now, and MythTV is fully functional.

---

