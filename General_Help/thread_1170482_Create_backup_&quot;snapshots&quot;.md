---
title: "Create backup &quot;snapshots&quot;"
date: 2009-05-26
forum: General Help
---

### Post by stevo81989 on 2009-05-26
Basically I am about to install a production level linux server. Once I get it installed and have a base configuration, I was wondering if there was a way I could take a snapshot of the machines state. So this way if I install something or something happens to it, I can just boot up with that image. Thanks for your help!!

---

### Post by Boondoklife on 2009-05-26
> **stevo81989 said:**
> Basically I am about to install a production level linux server. Once I get it installed and have a base configuration, I was wondering if there was a way I could take a snapshot of the machines state. So this way if I install something or something happens to it, I can just boot up with that image. Thanks for your help!!


Well the way I alway did it was to use dd to make an image of the disk and store it away, you could always use tar to do the same thing.

either way all you would need to do is boot off a cd and then restore the files. T youar would not take care of a HD crash though as it would not get the boot records I don't think, while dd should.

I would recommend doing either booted from said CD though. oh and dont mount the drive if you are doing a dd image. just dd from the /dev/sdx to a file. 

Downside to the dd is it makes an image of the ENTIRE drive, so you would need to have the space laying around. you can dd a partition but that again would leave you with the boot records issue.

There are other options though, this is just what I am familiar with.

---

### Post by Cheesemill on 2009-05-26
Take a look at CloneZilla.
[http://clonezilla.org/](http://clonezilla.org/)

Cheesemill

---

