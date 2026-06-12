---
title: "Adzapper with Squid in Ubuntu"
date: 2008-12-31
forum: General Help
---

### Post by Mezz8080 on 2008-12-31
Hi Everyone, 

This is my first post so if this is in the wrong place please move it. 

I am setting up a squid proxy using Ubuntu and trying to get Adzap to work using this guide [http://librenix.com/?inode=4483]("http://librenix.com/?inode=4483"). After following this guide when I try to restart the squid service I get the following message:

FATAL: Bungled squid.conf line 4557: redirect_program /usr/local/adzap/scripts/wrapzap
Squid Cache (Version 2.7.STABLE3): Terminated abnormally.

I checked the squid cache.log but it shows nothing. The squid.conf file is pretty standard with just the added line:

redirect_program /usr/local/adzap/scripts/wrapzap

I have also added a small bit for caching of youtube videos but I don't know if that would be affecting things.

I haven't been able to find anything via google so if anyone could provide any assistance it would be great.

Cheers,
Mezz

---

### Post by Mezz8080 on 2009-01-01
Got this sorted in the end. Look into using multiple re-directors if you come across the same problem and are running multiple things on your proxy, (in my case videocache and adzapper).

---

### Post by mynullvoid on 2009-07-02
Mezz8080, can you share with me how you managed to get adzapper and videocache working together?

I am running squid 2.7 (in my debian stable) and had followed all the guide in getting my videocache 1.9.1 to work with my wrapzap. Until now, the adzapper is not working, and there is no error shown. The videocache works.

If I comment videocache lines, then only adzapper work.

This is my line: [http://cachevideos.com/forum/post/squid-adzapper-videocache-not-working](http://cachevideos.com/forum/post/squid-adzapper-videocache-not-working)

Please assist. Thank you

---

### Post by Mezz8080 on 2009-07-02
Hey buddy.

I knew I should have written down how I got it working. I will have a look at it tomorrow night after work and try to find out how I did it again. That's if no one can help you in the mean time of course.

---

### Post by Mezz8080 on 2009-07-02
ok thought I would have a bit of a look at this tonight. Your wrapzap file looks good to me.

In your squid.conf file try the following..

change redirect_program /usr/bin/wrapzap to url_rewrite_program /usr/bin/wrapzap

I would also try commenting out the lines suggested in the thread you linked to above as I do have them commented out in my conf file.

Let me know how you go and I will have a good look at it tomorrow night when I am a bit more awake ;)

Mezz

---

